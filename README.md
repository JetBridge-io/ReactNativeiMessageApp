# ReactNativeiMessageApp
React Native enabled Xcode template for iMessage App using A380
<br>
<img src="https://github.com/JetBridge-io/ReactNativeiMessageApp/blob/master/screenshot/iMessage_with_A380.png" alt="iMessageApp with A380" width="200" />

ReactNativeiMessageApp is a Xcode template project for iMessage Application which has enabled the React Native and A380.

# How to

## Prerequisite ##
* Download repository
* Run [A380_backend](https://github.com/JetBridge-io/A380_backend).

* install brew, watchman
~~~
> /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
> brew update
> brew install watchman
~~~

## How to install ##
~~~
> cd ReactNativeiMessageApp/rnMessage
> npm install
> react-native link
~~~

### Set backend server address
* Run below command.
~~~~
> A380 server <http://youraddress:port>
~~~~

### Register ###
* `register` command will registers your react-native app to the server.

#### Command 
* Run below command from your react-native-app root folder where `package.json` reside.
~~~
> A380 register
Repository clone url : {Enter your github repository}
Repository - github token : {Enter your github token}
~~~
* Github token can be created from this [link.](https://help.github.com/articles/creating-an-access-token-for-command-line-use/)

### Release ###
* `release` command will pull your sources from the github and build it.

#### Command
* Run below command from your react-native-app root folder where `package.json` reside.
~~~
> A380 release <os>
~~~
where os should be `android` or `ios`.
* the A380 server will pull the git sources and build it.

### Deploy ###
* Once the app is ready to be published, use `deploy` command to simply do the job.

#### Command
* Run below command from your project root folder where `package.json` reside.
~~~~
> A380 deploy <os>
~~~~

### Run iOS App
#### Modify appkey and moduleName
* appKey be used as "AccesKey" in '.A380.config'.
* "AccessKey" can be confirmed by below command.
~~~
> cat .A380.config
~~~
* moduleName is equal to "name" in 'package.json'
* Open the Xcode project
* Modify appkey and moduleName in MessagesViewController.m
```objectivec
    NSString *appKey = @"YOUR_BUNDLEBUS_APP_KEY";
    A380 *A380 = [[A380 alloc] init];
    [A380 silentUpdate:appKey];
```
```objectivec
    RCTRootView *rootView = [[RCTRootView alloc] initWithBundleURL:jsCodeLocation
                                                        moduleName:@"YOUR_REACTNATIVE_APP_NAME"
                                                 initialProperties:nil
                                                     launchOptions:nil];

```
#### Build
* Build by Xcode
