# npm Plugin For TestCafe Integration With LambdaTest HyperExecute

[![Testcafe Health Check](https://github.com/LambdaTest/testcafe-browser-provider-hyperexecute/actions/workflows/main.yml/badge.svg)](https://github.com/LambdaTest/testcafe-browser-provider-hyperexecute/actions/workflows/main.yml)

This plugin integrates [TestCafe](http://devexpress.github.io/testcafe) with the [LambdaTest HyperExecute Testing Cloud](https://www.lambdatest.com/hyperexecute/).

## Install

```sh
$ npm install testcafe-browser-provider-hyperexecute
```

## Usage
Before using this plugin, save the LambdaTest username and access key to environment variables `LT_USERNAME` and `LT_ACCESS_KEY`, as described in [LambdaTest Documentation](https://www.lambdatest.com/support/docs/using-environment-variables-for-authentication-credentials).

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

 - `LT_TEST_NAME` - Test name on LambdaTest.
 - `LT_BUILD` - Build name on LambdaTest.
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

## About LambdaTest

[LambdaTest](https://www.lambdatest.com/) is a cloud based selenium grid infrastructure that can help you run automated cross browser compatibility tests on 2000+ different browser and operating system environments. LambdaTest supports all programming languages and frameworks that are supported with Selenium, and have easy integrations with all popular CI/CD platforms. It's a perfect solution to bring your [selenium automation testing](https://www.lambdatest.com/selenium-automation) to cloud based infrastructure that not only helps you increase your test coverage over multiple desktop and mobile browsers, but also allows you to cut down your test execution time by running tests on parallel.

## License

Licensed under the [MIT license](./LICENSE).
