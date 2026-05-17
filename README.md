# npm Plugin For TestCafe Integration With HyperExecute - TestMu AI (Formerly LambdaTest)

<p align="center">
  <a href="https://www.testmuai.com/"><img src="https://img.shields.io/badge/MADE%20BY%20TestMu%20AI-000000.svg?style=for-the-badge&labelColor=000" alt="Made by TestMu AI"></a>
  <a href="https://www.npmjs.com/package/testcafe-browser-provider-hyperexecute"><img src="https://img.shields.io/npm/v/testcafe-browser-provider-hyperexecute.svg?style=for-the-badge&labelColor=000000" alt="npm version"></a>
  <a href="https://community.testmuai.com/"><img src="https://img.shields.io/badge/Join%20the%20community-blueviolet.svg?style=for-the-badge&labelColor=000000" alt="Community"></a>
</p>

## Getting Started

[TestMu AI](https://www.testmuai.com/) (Formerly LambdaTest) is the world's first full-stack AI Agentic Quality Engineering platform that empowers teams to test intelligently, smarter, and ship faster. Built for scale, it offers a full-stack testing cloud with 10K+ real devices and 3,000+ browsers. With AI-native test management, MCP servers, and agent-based automation, TestMu AI supports Selenium, Appium, Playwright, and all major frameworks.

With TestMu AI (Formerly LambdaTest), you can use the npm plugin for running TestCafe tests with HyperExecute.

- [Sign up on TestMu AI](https://www.testmuai.com/register/) (Formerly LambdaTest).
- Follow the [TestMu AI Documentation](https://www.testmuai.com/support/docs/) for the full setup walkthrough.
  
## Install

```sh
$ npm install testcafe-browser-provider-hyperexecute
```

## Usage
Before using this plugin, save the TestMu AI (Formerly LambdaTest) username and access key to environment variables `LT_USERNAME` and `LT_ACCESS_KEY`, as described in TestMu AI (Formerly LambdaTest) Documentation.

You can determine the available browser aliases by running

```sh
$ testcafe -b hyperexecute
```

If you run tests from the command line, use the browser alias when specifying browsers:
For Single Configuration

```sh
$ testcafe "hyperexecute:Chrome@74.0:Windows 8" "path/to/test/file.js"
```

For Parallel/Multiple Configuration

```sh
$ testcafe "hyperexecute:Chrome@74.0:Windows 8","hyperexecute:Chrome@75.0:Windows 10" "path/to/test/file.js"
```

For Real Devices
```sh
$ testcafe "hyperexecute:Galaxy S8@9:android:isReal" "path/to/test/file.js"
```


```
Not valid for real Devices: ---
                              v
```
When you use API, pass the alias to the `browsers()` method:

```js
testCafe
    .createRunner()
    .src('path/to/test/file.js')
    .browsers('hyperexecute:Chrome@74.0:Windows 8')
    .run();
```

## Build Plugin Locally (Development Mode)

1.  Clone this repository,
2.  Rename Project
```sh
$ mv testcafe-browser-provider-hyperexecute hyperexecute
```
3. Go to the project path
```sh
$ cd hyperexecute
```
4. Install Packages and Build
```sh
$ npm i
$ npm run build
```
5. Link Testcafe with hyperexecute
```sh
$ sudo npm link
```
6. [See this for Credentials](#usage)

## Configuration

Use the following environment variables to set additional configuration options:

 - `LT_TEST_NAME` - Test name on TestMu AI (Formerly LambdaTest).
 - `LT_BUILD` - Build name on TestMu AI (Formerly LambdaTest).
 - `LT_CAPABILITY_PATH` - Path to a file which contains additional capability options as JSON file (eg. config.json)

    ```js
    {
        "Chrome@63.0:Windows 8.1": {
            "network": true,
            "visual": true,
            "timezone": "UTC+11:00"
        }
    }
    ```
    - `Chrome@63.0:Windows 8.1` is browser alias.
 - `LT_RESOLUTION` - allows setting the screen resolution for desktop browsers in the `${width}x${height}` format.
 - `LT_VERBOSE` - true or false.
 - `LT_W3C` - true or false.
 - `LT_ENABLE_TRACE` - true or false.
 - `LT_PROXY_HOST` - Hostname/IP of proxy, this is a mandatory value.
 - `LT_PROXY_PORT` - Port for the proxy, by default it would consider 3128 if proxyhost is used For Basic Authentication, we use the below proxy options.
 - `LT_PROXY_USER` - Username for connecting to proxy, mandatory value for using 'proxypass'.
 - `LT_PROXY_PASS` - Password for the USERNAME option.
 - `LT_DIR` - Path of the local folder you want to test.
 - `LT_SELENIUM_VERSION` - Browser specific capability (Not for Real Devices)
 - `LT_APPIUM_VERSION` - Real Device specific capability
 - `LT_CONSOLE` - true or false.
 - `LT_NETWORK` - true or false.
 - `LT_VIDEO` - true or false.
 - `LT_SCREENSHOT` - true or false.
 - `LT_TIMEZONE` - Configure tests to run on a custom time zone. (Not for Real Devices)

Example:

```sh
export LT_RESOLUTION="1920x1080"
export LT_TEST_NAME="Test TestCafe"
export LT_BUILD="Build x"
testcafe "hyperexecute:Chrome","hyperexecute:Chrome@74.0:Windows 8" tests/
```

```
LT_TIMEZONE
LT_SELENIUM_VERSION
LT_RESOLUTION

Above are not valid for real devices
```

## About TestMu AI (Formerly LambdaTest)

TestMu AI (Formerly LambdaTest) is the world's first full-stack AI Agentic Quality Engineering platform that empowers teams to test intelligently, smarter, and ship faster. Built for scale, it offers a full-stack testing cloud with 10K+ real devices and 3,000+ browsers. With AI-native test management, MCP servers, and agent-based automation, TestMu AI (Formerly LambdaTest) supports Selenium, Appium, Playwright, and all major frameworks.

## License

Licensed under the [MIT license](./LICENSE).

## LambdaTest is Now TestMu AI

On **January 12, 2026**, [LambdaTest evolved to TestMu AI](https://www.testmuai.com/lambdatest-is-now-testmuai/), the world's first fully autonomous **Agentic AI Quality Engineering Platform**.

Same team. Same infrastructure. Same customer accounts. All existing LambdaTest logins, scripts, capabilities, and integrations continue to work without change.

ð Find the new home for [LambdaTest](https://www.testmuai.com).

### How LambdaTest Evolved into TestMu AI

In 2017, we launched LambdaTest with a simple mission: make testing fast, reliable, and accessible. As LambdaTest grew, we expanded into Test Intelligence, Visual Regression Testing, Accessibility Testing, API Testing, and Performance Testing, covering the full depth of the testing lifecycle.

As software development entered the AI era, testing had to evolve, too. We rebuilt the architecture to be AI-native from the ground up, with autonomous agents that **plan, author, execute, analyze, and optimize tests** while keeping humans in the loop. The platform integrates with your repos, CI, IDEs, and terminals, continuously learning from every code change and development signal.

That evolution earned a new name: **TestMu AI**, built for an AI-first future of quality engineering. TestMu is not a new name for us. It is the name of our annual community conference, which has brought together 100,000+ quality engineers to discuss how AI would reshape testing, long before that became an industry norm. 

What started as a high-performance cloud testing platform has transformed into an AI-native, multi-agent system powering a connected, end-to-end quality layer. That evolution defined a new identity: LambdaTest evolved into TestMu AI, built for an AI-first future of quality engineering.

## Support

Got a question? Email [support@testmuai.com](mailto:support@testmuai.com) or chat with us 24x7 from our chat portal.
