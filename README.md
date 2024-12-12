## Project overview

This blueprint creates a [Vue](https://vuejs.org/) SPA (single-page application) project. The project uses the CodeCatalyst Labs action "Deploy to AWS Amplify Hosting" to deploy to [AWS Amplify Hosting](https://aws.amazon.com/amplify/hosting/).

### Architecture overview

A (SPA) single-page application is a web application implementation that loads a web document and updates it by using JavaScript APIs. Your customers can then use your website without loading entire pages from the server, which helps improve your website's performance and provides a more dynamic user experience. 

The deployment pipeline deploys the SPA to an Amazon CodeCatalyst environment. The Amazon CodeCatalyst environment requires an AWS account connection for your Amazon CodeCatalyst space and a configured IAM role for your project workflow. After you create your project, you can view the repository, source code, and CI/CD workflow for your Amazon CodeCatalyst project. After your workflow runs successfully, you can access your deployed application URL in the output of your workflow.

### Web application framework

**[Vue](https://vuejs.org/)** - powered by [create-vue](https://github.com/vuejs/create-vue)

### Hosting



**AWS Amplify Hosting**

[AWS Amplify Hosting](https://aws.amazon.com/amplify/hosting/) offers a fully managed hosting service for web apps and static websites that can be accessed directly from the AWS console.

![AWS Amplify Architecture Diagram](https://deyn4asqcu6xj.cloudfront.net/create-spa-amplify-hosting.png)

## Connections and permissions

You can create a new account connection from the AWS accounts menu in your Amazon CodeCatalyst space. AWS IAM roles added to the account connection are used to authorize project workflows to access AWS account resources.

Expected role capabilities: *CodeCatalyst**

## Project resources

This project contains the following folders:

- root - The web application

This project has created the following Amazon CodeCatalyst Resources:

- A source repository
- An environment
- A workflow for verifying pull requests at .codecatalyst/workflows/onPullRequestBuildAndTest.yaml
- A workflow for deploying changes pushed to main at .codecatalyst/workflows/onPushToMainPipeline.yaml

### Cleaning up resources

To cleanup the resources created by this project delete the stack that the "Deploy to AWS Amplify Hosting" action created. To delete the stack use the AWS CloudFormation console in the AWS account you associated when you launched the blueprint. To find the stack name refer to the workflow, if you used the default stack name it will be DevelopmentFrontendStack-XXXXX.

## Additional resources

See the Amazon CodeCatalyst user guide for additional information on using the features and resources of Amazon CodeCatalyst

---

# spa-app

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

## Type Support for `.vue` Imports in TS

TypeScript cannot handle type information for `.vue` imports by default, so we replace the `tsc` CLI with `vue-tsc` for type checking. In editors, we need [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin) to make the TypeScript language service aware of `.vue` types.

If the standalone TypeScript plugin doesn't feel fast enough to you, Volar has also implemented a [Take Over Mode](https://github.com/johnsoncodehk/volar/discussions/471#discussioncomment-1361669) that is more performant. You can enable it by the following steps:

1. Disable the built-in TypeScript Extension
   1. Run `Extensions: Show Built-in Extensions` from VSCode's command palette
   2. Find `TypeScript and JavaScript Language Features`, right click and select `Disable (Workspace)`
2. Reload the VSCode window by running `Developer: Reload Window` from the command palette.

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
yarn
```

### Compile and Hot-Reload for Development

```sh
yarn dev
```

### Type-Check, Compile and Minify for Production

```sh
yarn build
```

### Run Unit Tests with [Vitest](https://vitest.dev/)

```sh
yarn test:unit
```

### Run End-to-End Tests with [Cypress](https://www.cypress.io/)

```sh
yarn test:e2e:dev
```

This runs the end-to-end tests against the Vite development server.
It is much faster than the production build.

But it's still recommended to test the production build with `test:e2e` before deploying (e.g. in CI environments):

```sh
yarn build
yarn test:e2e
```

### Lint with [ESLint](https://eslint.org/)

```sh
yarn lint
```
