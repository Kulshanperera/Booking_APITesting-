**Chapter 04**

* Install Newman

_installation_

**$ npm install -g newman //newman --version - check Version**

* Execute postman collection using Newman

**$ newman run collectionFileName.json -e environmenrVariableFileName.json  //run collection using CMD -e including an environment file**

* generate standard html report using Newman

Reporters with Newman Install the reporter package

$ npm install -g newman-reporter-html //simple report

_Run_

**$ newman run /path/to/collection.json -r cli,html**

Reporters with Newman Install the reporter package

**$ npm install -g newman-reporter-html //simple report**

_Run_

**$ newman run /path/to/collection.json -r cli,html**

* generate detailed report using Newman

Interactive Example report

To globally install the htmlextra package:

**$ npm install -g newman-reporter-htmlextra**

excute collection using advance HTML report

**$ newman run collectionName.json -r htmlextra --reporters-cli,htmlextra**
