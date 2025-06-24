# Contributing to Gravatar

🤗 Welcome, and thank you for your interest in Gravatar! Whether you're here to report an issue, suggest a new feature, or submit code changes, we greatly appreciate your help.

## Questions, Issue Reporting, and Feature Suggestions

Please [submit an issue](https://github.com/Automattic/gravatar/issues/new/choose) with all pertinent details and context to help us fully understand your report or suggestion. To avoid duplication, kindly check for existing issues or feature requests similar to yours before filing a new one.

## Code Contributions

We welcome Pull Requests, particularly for bug fixes related to any open issues you wish to address! If you're new to creating Pull Requests, we suggest you check out [this free video series](https://egghead.io/courses/how-to-contribute-to-an-open-source-project-on-github).

The Gravatar packages are developed using [TypeScript](https://www.typescriptlang.org/), [Sass](https://sass-lang.com/) (following [BEM naming conventions](https://getbem.com/)), and is bundled using [Webpack](https://webpack.js.org/). For package management and script running, we use [npm](https://www.npmjs.com/).

### Development Workflow

The general development workflow is as follows:

1. Fork and clone the repository.
2. Install the dependencies by running `npm install`. Make sure your Node version matches the minimum requirement specified in the `package.json` file.
3. Create a new branch, using [the branch naming scheme](https://github.com/Automattic/wp-calypso/blob/trunk/docs/git-workflow.md#branch-naming-scheme), e.g. `add/a-cool-feature` or `fix/100-a-bug`.
4. Navigate to the project directory by running `cd web/packages/[package-name]`.
5. Build the library in development mode using `npm run build:watch`. This command compiles the code and watches for changes.
6. **In a new terminal**, start a local server with `npm run start`. Now you can modify the code in the `src` folder and test it (or the output formats) in the `playground` directory.
7. Update or add the related types if necessary.
8. If needed, update the relevant documentation.
9. Commit your changes and check if all the automated tests pass. (You can fix linting errors by running `npm run lint:<TYPE> --fix`)
10. Create a Pull Request with your changes.

### Scripts

Below is a list of commonly used scripts. You can run them using `npm run <script>`:

- `start`: Starts a local server to test the library in development mode.
- `build`: Builds the library in production mode, creating the `dist` folder with bundled files.
- `build:dev`: Builds the library in development mode, creating the `dist` folder with bundled files.
- `build:watch`: Builds the library in development mode and watches for changes.
- `format`: Formats the code using the [`format`](https://developer.wordpress.org/block-editor/reference-guides/packages/packages-scripts/#format) script of `@wordpress/scripts`.
- `type-check`: Checks the types using [TypeScript](https://www.typescriptlang.org/).
- `lint:js`: Lints the JavaScript / TypeScript code using the [`lint:js`](https://developer.wordpress.org/block-editor/reference-guides/packages/packages-scripts/#lint-js) script of `@wordpress/scripts`.
- `lint:style`: Lints the Sass / CSS code using the [`lint:style`](https://developer.wordpress.org/block-editor/reference-guides/packages/packages-scripts/#lint-style) script of `@wordpress/scripts`.
- `lint:md:docs`: Lints the Markdown files using the [`lint:md:docs`](https://developer.wordpress.org/block-editor/reference-guides/packages/packages-scripts/#lint-md-docs) script of `@wordpress/scripts`.
- `lint`: Runs all the linters.
- `clean:dist`: Removes the `dist` folder.
- `clean:release`: Removes the `release` folder.
- `clean`: Removes all the generated folders (e.g. `dist`, `release`).
- `release`: Creates a new release of the library.

### PR Merge Policy

- Pull Requests (PRs) must pass all automated tests and receive approval from at least one reviewer before they can be merged into the `trunk` branch.
- Who is responsible for merging the approved PRs?
    - For PRs authored by external individuals who do not have push permissions, the reviewer who approved the PR will handle the merging process.
    - For PRs authored by contributors who have push permissions, the author of the PR will merge their own PR.

## Release Process

This project utilizes [release-it](https://github.com/release-it/release-it) for automating releases across both [NPM](https://www.npmjs.com/~gravatar-automattic) and [GitHub](https://github.com/Automattic/gravatar/releases). There're two ways to create a new release:

- GitHub Action:
    - Go to [the GitHub actions page](https://github.com/Automattic/gravatar/actions)
    - Select the package you want to release from the list of workflows on the left side
    - Select the appropriate workflow on the left side
    - Click on the `Run workflow` button
    - Choose the appropriate `Version type` (we use [Semantic Versioning](https://semver.org/))
    - Confirm by clicking on `Run workflow` again
- Local Release (with the push permission): Navigate to the `web/packages/[package-name]` folder, run `npm run release`, and follow the instructions.

After the package is released, review [the release notes](https://github.com/Automattic/gravatar/releases) and make any necessary modifications.
随时随地编辑您的 Gravatar 个人资料

虽然 Gravatar 支持用户在网络上使用头像和个人资料，但个人资料编辑功能此前仅限于 Gravatar.com。快速编辑器可将个人资料编辑功能直接引入您的应用程序。

Gravatar 快速编辑器是一个 JavaScript 库，允许用户将 Gravatar 快速编辑器集成到他们的 Web 应用程序中，从而通过弹出窗口轻松编辑 Gravatar 个人资料。该库提供了一个用于高级控制的核心类和一个用于快速设置的简化类。

工作原理

快速编辑器遵循熟悉的 OAuth 风格流程，类似于 PayPal 或 Stripe 等支付服务提供商的流程：

用户点击应用程序中的编辑按钮

身份验证弹出窗口要求输入电子邮件和验证码

用户编辑他们的个人资料（头像、个人简介、位置、社交链接……——您定义功能集）

用户关闭弹出窗口，并返回到您的应用程序并更新个人资料

您可以控制用户可以查看和编辑哪些个人资料元素。界面清晰地显示更改会影响用户的全局 Gravatar 个人资料。用户个人资料更改会在所有支持 Gravatar 的平台上自动同步。

 WordPress 中的 Gravatar 快速编辑器集成

简化头像和个人资料管理

Gravatar 非常适合预填个人资料数据并显示默认头像，但用户希望直接编辑个人资料和图片。传统平台必须从头开始构建自己的图片上传和个人资料编辑系统。快速编辑器免除了这一负担——用户无需构建任何自定义基础架构即可更新头像。

最重要的是，用户会留在您的网站上。他们可以在网站上编辑个人资料，然后返回继续之前的操作，不会受到任何干扰。

入门

使用 NPM 或 Yarn 安装

使用 npm 或 yarn 安装包：

npm install @gravatar-com/quick-editor

yarn add @gravatar-com/quick-editor

用法

Gravatar快速编辑器

该类 GravatarQuickEditor 通过自动设置事件处理程序来打开弹出窗口并更新页面上的头像元素，从而简化了设置过程。

例子

import { GravatarQuickEditor } from '@gravatar-com/quick-editor';

document.addEventListener( 'DOMContentLoaded', () => {
 new GravatarQuickEditor( {
 email: 'user@example.com',
 editorTriggerSelector: '#edit-profile',
 avatarSelector: '#gravatar-avatar',
 scope: [ 'avatars' ],
 } );
} );

GravatarQuickEditorCore

该类 GravatarQuickEditorCore 提供对 Gravatar 快速编辑器功能的高级控制，允许开发人员触发弹出事件并设置配置文件更新回调。

例子

import { GravatarQuickEditorCore } from '@gravatar-com/quick-editor';

document.addEventListener( 'DOMContentLoaded', () => {
 const quickEditorCore = new GravatarQuickEditorCore( {
 email: 'user@example.com',
 scope: [ 'avatars', 'about' ],
 onProfileUpdated: () => {
 console.log( 'Profile updated!' );
 },
 onOpened: () => {
 console.log( 'Editor opened!' );
 },
 } );

 document.getElementById( 'edit-profile' ).addEventListener( 'click', () => {
 quickEditorCore.open();
 } );
} );

API

欲了解更多信息，请访问我们的 GitHub 存储库查看 API 文档。

Gravatar 快速编辑器
