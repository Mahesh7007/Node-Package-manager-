# npm
### A JavaScript PDF generation library for NodeJs

- Step 1 - Add required packages and read HTML template
```html
var pdf = require("pdf-node");
var fs = require("fs");

var html = fs.readFileSync("template.html", "utf8");
```
- Step 2 - Create your HTML Template
![logo](https://github.com/Mahesh7007/Node-Package-manager-/blob/main/html_template.png)

- Step 3 - Provide format and orientation as per your need
  ```html
   var options = {
        format: "A3",
        orientation: "portrait",
        border: "10mm",
        header: {
            height: "45mm",
            contents: '<div style="text-align: center;">Author: Shyam Hajare</div>'
        },
        footer: {
            height: "28mm",
            contents: {
                first: 'Cover page',
                2: 'Second page', // Any page number is working. 1-based index
                default: '<span style="color: #444;">{{page}}</span>/<span>{{pages}}</span>', // fallback value
                last: 'Last Page'
            }
        }
    };
  ```

  - Step 4 - Provide HTML, user data and PDF path for output
```html
var users = [
    {
      name: "Mahesh",
      age: "21",
    },
    {
      name: "Jone",
      age: "23",
    },
    {
      name: "Dhoni",
      age: "29",
    },
  ];
  var document = {
    html: html,
    data: {
      users: users,
    },
    path: "./output.pdf",
    type: "pdf",
  };
```
- Step 5- After setting all parameters, just pass document and options to pdf.create method
```html
pdf(document, options)
  .then((res) => {
    console.log(res);
  })
  .catch((error) => {
    console.error(error);
  });
```
