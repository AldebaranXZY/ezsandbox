# Koii Task Template

This is the new K2 Task Template which uses Webpack to allow support of all node modules and project structures instead of a single file executable for the Koii task. [WIP]

## How to use

1. Clone this repo
2. Run `npm install`
3. Run `npm run test` for Jest testing or `node prod-debug.js` for live debugger

## Structure explain

The task template contains three separate JavaScript files in the task folder that contain all of the functions for a Koii task to function properly.

```bash
📦K2-TASK-TEMPLATE
 ┣ 📂_koiiNode
 ┃ ┗ 📜koiiNode.js // Contain all the components that task connect to K2.
 ┣ 📂task
 ┃ ┣ 📜index.js // Main file that contains the task function.
 ┃ ┣ 📜submission.js // Contains the task function and submitTask function.
 ┃ ┣ 📜audit.js // Contains the auditTask function.
 ┃ ┗ 📜distribution.js // Contains the submitDistributionList and auditDistribution function.
 ┣ 📂tests
 ┣ 📜config-task.yml
 ┣ 📜coreLogic.js
 ┗ 📜index.js
```

## What's in the template

### Core files

- index.js — is the hub of your app, and ties the other pieces together. This will be the entry point when your task runs on task nodes.

- \_koiiNode — is a directory that contains koiiNode.js which has the interfaces to make API calls to the core of the task node. It contains all the necessary functions required to submit and audit the work, as well as the distribution lists. Check [here](https://docs.koii.network/develop/write-a-koii-task/task-development-kit-tdk/using-the-task-namespace/the-namespace-object) to learn more about namespace functions.

### Task Directory

It houses three key files: submission.js, audit.js and distribution.js. These files are where you define your task, audit, and distribution logic, enabling you to control the core functionality of the task.

This structure allows a modular approach to task development. By only utilizing these three files, you can easily modify and test your task logic without having to worry about the other aspects. To understand the theory behind this, please refer to the
[Runtime Flow](https://docs.koii.network/concepts/gradual-consensus/runtime-flow).

Finally, in the index.js file, all these functions are combined as a task, which is then imported and used in corelogic.js. It is advisable to organize separate features into sub-files and import them into the relevant files before web-packing for better code management and maintainability. This modular approach allows for a more organized and efficient development process.

For more information about how to customize your own task, please check our docs [here](https://docs.koii.network/develop/write-a-koii-task/task-development-guide/introduction).
