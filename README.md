# Java Cucumber With Appium — TestMu AI (Formerly LambdaTest)
![pw](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=java&logoColor=white)


<p align="center">
  <a href="https://www.testmuai.com/blog/?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-java-cucumber" target="_bank">Blog</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.testmuai.com/support/docs/?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-java-cucumber" target="_bank">Docs</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.testmuai.com/learning-hub/?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-java-cucumber" target="_bank">Learning Hub</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.testmuai.com/newsletter/?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-java-cucumber" target="_bank">Newsletter</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.testmuai.com/certifications/?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-java-cucumber" target="_bank">Certifications</a>
  &nbsp; &#8901; &nbsp;
  <a href="https://www.youtube.com/@TestMuAI" target="_bank">YouTube</a>
</p>
&emsp;
&emsp;
&emsp;

_Appium is a tool for automating native, mobile web, and hybrid applications on iOS, Android, and Windows platforms. It supports iOS native apps written in Objective-C or Swift and Android native apps written in Java or Kotlin. It also supports mobile web apps accessed using a mobile browser (Appium supports Safari on iOS and Chrome or the built-in 'Browser' app on Android). Perform Appium automation tests on [TestMu AI's online cloud](https://www.testmuai.com/appium-mobile-testing)._

*Learn the basics of [Appium testing on the TestMu AI platform](https://www.testmuai.com/support/docs/getting-started-with-appium-testing/?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-java-cucumber).*

[<img height="53" width="200" src="https://user-images.githubusercontent.com/70570645/171866795-52c11b49-0728-4229-b073-4b704209ddde.png">](https://accounts.lambdatest.com/register?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-java-cucumber)

## Table of Contents

- [Pre-requisites](#pre-requisites)
- [Run Your First Test](#run-your-first-test)
- [Executing The Test](#executing-the-test)

## Pre-requisites

Before you can start performing App automation testing with Appium, you would need to follow these steps:

- Ensure you have the [Java client library](https://github.com/appium/java-client) installed for Selenium and Appium.
- Install the latest Java development environment i.e. JDK 8 or higher. We recommend using the < JDK 11 version.
- Download and install **Maven** following the steps from [the official website](https://maven.apache.org/). Maven can also be installed easily on **Linux/MacOS** using [**Homebrew**](https://brew.sh/) package manager.

### Clone The Sample Project

Clone the TestMu AI’s :link: [LT-appium-java-cucumber](https://github.com/LambdaTest/LT-appium-java-cucumber) repository and navigate to the code directory as shown below:

```js
git clone https://github.com/LambdaTest/LT-appium-java-cucumber
cd LT-appium-java-cucumber
```

### Setting Up Your Authentication

Make sure you have your TestMu AI credentials with you to run test automation scripts on LambdaTest. To obtain your access credentials, [purchase a plan](https://billing.lambdatest.com/billing/plans?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-java-cucumber) or access the [Automation Dashboard](https://appautomation.lambdatest.com/?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-java-cucumber).

Set TestMu AI `Username` and `Access Key` in environment variables.

**For Linux/macOS:**

```js
export LT_USERNAME=YOUR_LAMBDATEST_USERNAME \
export LT_ACCESS_KEY=YOUR_LAMBDATEST_ACCESS_KEY
```

**For Windows:**

```js
set LT_USERNAME=YOUR_LAMBDATEST_USERNAME `
set LT_ACCESS_KEY=YOUR_LAMBDATEST_ACCESS_KEY
```

### Upload Your Application

Upload your **_iOS_** application (.ipa file) or **_android_** application (.apk file) to the TestMu AI servers using our **REST API**. You need to provide your **Username** and **AccessKey** in the format `Username:AccessKey` in the **cURL** command for authentication. Make sure to add the path of the **appFile** in the cURL request. Here is an example cURL request to upload your app using our REST API:

**Using App File:**

**Linux/macOS:**

```js
curl -u "YOUR_LAMBDATEST_USERNAME:YOUR_LAMBDATEST_ACCESS_KEY" \
--location --request POST 'https://manual-api.lambdatest.com/app/upload/realDevice' \
--form 'name="Android_App"' \
--form 'appFile=@"/Users/macuser/Downloads/proverbial_android.apk"'
```

**Windows:**

```js
curl -u "YOUR_LAMBDATEST_USERNAME:YOUR_LAMBDATEST_ACCESS_KEY" -X POST "https://manual-api.lambdatest.com/app/upload/realDevice" -F "appFile=@"/Users/macuser/Downloads/proverbial_android.apk""
```

**Using App URL:**

**Linux/macOS:**

```js
curl -u "YOUR_LAMBDATEST_USERNAME:YOUR_LAMBDATEST_ACCESS_KEY" \
--location --request POST 'https://manual-api.lambdatest.com/app/upload/realDevice' \
--form 'name="Android_App"' \
--form 'url="https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk"'
```

**Windows:**

```js
curl -u "YOUR_LAMBDATEST_USERNAME:YOUR_LAMBDATEST_ACCESS_KEY" -X POST "https://manual-api.lambdatest.com/app/upload/realDevice" -d "{"url":"https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk","name":"sample.apk"}"
```

**Tip:**

- If you do not have any **.apk** or **.ipa** file, you can run your sample tests on TestMu AI by using our sample :link: [Android app](https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_android.apk) or sample :link: [iOS app](https://prod-mobile-artefacts.lambdatest.com/assets/docs/proverbial_ios.ipa).
- Response of above cURL will be a **JSON** object containing the `App URL` of the format - <lt://APP123456789123456789> and will be used in the next step.

## Run Your First Test

**Test Scenario:** Check out [TestRunner.java](https://github.com/LambdaTest/LT-appium-java-cucumber/blob/master/src/main/java/MyRunner/TestRunner.java) file to view the sample test script.

### Configuring Your Test Capabilities

You can update your custom capabilities in test scripts. In this sample project, we are passing platform name, platform version, device name and app url (generated earlier) along with other capabilities like build name and test name via capabilities object.
Check out [single.xml](https://github.com/LambdaTest/LT-appium-java-cucumber/blob/master/single.xml/) for single tests and [parallel.xml](https://github.com/LambdaTest/LT-appium-java-cucumber/blob/master/parallel.mxl) for parallel test capabilities. The capabilities object in the sample code are defined as:


```java
    DesiredCapabilities capability = new DesiredCapabilities();    		
        capability.setCapability("platformName", platformName);
        capability.setCapability("deviceName", deviceName);
        capability.setCapability("platformVersion",platformVersion);
    		    		
    		capability.setCapability("build", "Native App automate Demo");
        capability.setCapability("test", "Test Parallel");    		
        capability.setCapability("isRealMobile", true);

        capability.setCapability("app","lt://proverbial-android");     //Enter the app url here
        capability.setCapability("network", true);
    		capability.setCapability("video", true);
    		capability.setCapability("console", true);
    		capability.setCapability("visual", true);
```

**Note:**

- You must add the generated **APP_URL** to the `"app"` capability in the config file.
- You can generate capabilities for your test requirements with the help of our inbuilt **[Capabilities Generator tool](https://www.testmuai.com/capabilities-generator/beta/index.html?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-java-cucumber)**. A more Detailed Capability Guide is available [here](https://www.testmuai.com/support/docs/desired-capabilities-in-appium/?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-java-cucumber).

## Executing The Test

Execute the following commands to install the required dependencies:

```bash
mvn clean install
```

The tests can be executed in the terminal using the following command:

**Single Test:**

```bash
mvn test -D suite=single.xml
```

**Parallel Test:**

```bash
mvn test -D suite=parallel.xml
```

**Info:** Your test results would be displayed on the test console (or command-line interface if you are using terminal/cmd) and on the :link: [TestMu AI App Automation Dashboard](https://appautomation.lambdatest.com/build?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-java-cucumber).

## Additional Links

- [Advanced Configuration for Capabilities](https://www.testmuai.com/support/docs/desired-capabilities-in-appium/?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-java-cucumber)
- [How to test locally hosted apps](https://www.testmuai.com/support/docs/testing-locally-hosted-pages/?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-java-cucumber)
- [How to integrate TestMu AI with CI/CD](https://www.testmuai.com/support/docs/integrations-with-ci-cd-tools/?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-java-cucumber)

## Documentation & Resources :books:

Visit the following links to learn more about TestMu AI's features, setup and tutorials around test automation, mobile app testing, responsive testing, and manual testing.

- [TestMu AI Documentation](https://www.testmuai.com/support/docs/?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-java-cucumber)
- [TestMu AI Blog](https://www.testmuai.com/blog/?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-java-cucumber)
- [TestMu AI Learning Hub](https://www.testmuai.com/learning-hub/?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-java-cucumber)

## TestMu AI Community :busts_in_silhouette:

The [TestMu AI Community](https://community.testmuai.com/?utm_source=github&utm_medium=repo&utm_campaign=LT-appium-java-cucumber) allows people to interact with tech enthusiasts. Connect, ask questions, and learn from tech-savvy people. Discuss best practises in web development, testing, and DevOps with professionals from across the globe 🌎

## What's New At TestMu AI ❓

To stay updated with the latest features and product add-ons, visit [Changelog](https://changelog.lambdatest.com/)

## 🚀 [LambdaTest is Now TestMu AI](https://www.testmuai.com/lambdatest-is-now-testmuai/)

👋 Welcome to TestMu AI, the next evolution of LambdaTest. As of January 2026, LambdaTest has officially rebranded to TestMu AI. We have evolved from a cross-browser testing cloud into a unified, AI-native quality engineering platform designed for the modern DevOps era.

Whether you have been part of the LambdaTest community for years or are just discovering TestMu AI, our mission remains the same: to help you ship faster with high-scale test execution, autonomous testing, and deep quality analytics.

**🔄 Our Rebrand Journey**

We chose the name TestMu AI to reflect our shift towards intelligent, autonomous testing. While our identity has changed, our core technology and commitment to the testing community stay the same.

**✨ Specialties**

- 🤖 AI-Native Test Execution (Formerly LambdaTest)
- ⚡ Autonomous Test Automation
- 🌐 Cross-Browser & Mobile Testing
- 📊 Unified Quality Intelligence

👉 Find [LambdaTest's New Home](https://www.testmuai.com/).