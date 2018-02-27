# Admin Panel

The OmiseGO Wallet admin panel for a provider to manage staff, users, roles and permissions, API access, minted tokens, transactions, etc.

## Usage

### Development

You will first need to create the `.env` file located under the project's root directory with your own keys.
`OMISEGO_BASE_URL` is your eWallet server url.
`OMISEGO_API_KEY_ID` and `OMISEGO_API_KEY` are the access keys corresponding to your Admin API.

Example **.env** file
```
ADMIN_PANEL_BASE_DIR=ADMIN_PANEL_BASE_DIR
API_BASE_URL=API_BASE_URL
API_KEY_ID=YOUR_API_KEY_ID
API_KEY=YOUR_API_KEY
```

### Running the Admin Panel

The Admin Panel will be started along with the whole umbrella app.
There are no extra steps required to start the Admin Panel.

### Tests

Run tests using the command below.

```shell
yarn test
```

or if you want to run tests on every file change:

```shell
yarn test:watch
```

## Development

### Front End Build Pipeline

The build pipeline can be broken down into 2 major steps: 1) **[Yarn](https://yarnpkg.com)** installs the project's dependencies, 2) **[Webpack](https://webpack.js.org)** then orchestrates other packages and plugins to do the build for it. It then bundles up the built files together, and ready them to be served to the client.

To add a new step to the build pipeline, the easiest to do is to find a webpack loader/plugin that does the job, then add it to the current webpack pipeline (in `config/webpack.js`).

***Note:** The purpose of this section is to illustrate the major steps that source files go through until being served to the client, not to detail each and every build steps performed. There may be other tools used in between the pipeline steps that are not mentioned here.*

1. **Yarn**: Install dependencies and manage yarn command aliases
2. **Webpack**: Bundle assets together into small packages to optimize load time.
    1. **babel-loader**: Use Babel to compile modern JavaScript down for compatibility with older browsers
    2. **uglifyjs-webpack-plugin**: Minify JavaScript files for efficiency
    3. **html-webpack-plugin**: Generate the html that serves the built files
    4. **webpack-dev-server**: Serve the files to the browser. Its trick is it monitors source file changes, rebuilds them, then automatically refreshes the browser with the built files.

### Directory Structure

```text
assets/
  ├─ config/          The folder for storing app and library configs
  ├─ node_modules/    [Autogenerated. Do not edit.] Node dependencies
  ├─ public/          Asset files that do not need to be processed. Your images, icons, fonts, videos and other static files should go here.
  ├─ src/             Source files that need to be processed. Your JS, JSX, EJS files should go here.
  ├─ stories/         Source files for the stories.
  ├─ __tests__/       Test files.
  ├─ .gitignore       The list of files and folders that git should ignore
  ├─ package.json     The manifest that contains project's metadata, dependencies, etc.
  ├─ README.md        The document you are currently reading explaining how to get started
  ├─ yarn.lock        [Autogenerated. Do not edit.] Yarn lockfile
  └─ .babelrc         The babelrc config file
```

Jumping onto the project? Get started by reading `package.json`, `config/webpack.js`, then jump onto `src/index.js`, the JS entrypoint of the project.