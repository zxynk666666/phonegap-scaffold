## This is a scaffold for building phonegap application
Phonegap is a tool to let developer build cross platform native mobile applciations using js/html/css. However, for morden web/UI developers, raw css/js/html are not preferable. We'd like to use scss/coffeescript/haml which are more efficient. 

Searching sometime, I haven't found any mature solutions yet, So I create this repo to let developers start building phonegap using morden tech as fast as possiable. 

It can
* detect your changes and compile it at the same time
* integrate jasmine as js test
* help to ajust style in brower and deploy it automatically to simulator  

## Prepare

* Of course, you need to download phonegap package first.
* If you want to build ios, make sure you have Xcode installed - with command line tools. 
* If you want to build android, make sure you have latest android SDK installed. Set ANDROID_HOME in your environment and adb/android can be found in command line.
* Install qt to run jasmine:headless. brew install qt 

## How to use(Take IOS for example)

* Open index.html in ios simulator. The following commands will open ios simulator and show index.html.
  
  Please replace *PHONEGAP_PATH* with your own path

  ```bash
  git clone git@github.com:warmwind/phonegap-scaffold.git
  PHONEGAP_PATH/lib/ios/bin/create phonegap-scaffold/platform/ios package_name phonegap
  cd phonegap-scaffold
  bundle
  rake set_env
  rake compile_all
  rake ios:run
  ```

* Open index.html in browser

  ```bash
  git clone git@github.com:warmwind/phonegap-scaffold.git
  cd phonegap-scaffold
  bundle
  rake set_env
  rake compile_all
  open www/index.html
  ```

## Development

### Auto Compile
Run guard to auto compile coffee, scss, haml
  ```bash
  guard
  ```

### Different Environment
  Maybe you are responable to build backend api as well as mobile, and your api has different urls for deveolopment, uat and production. Run the following task to set env for phonegap application

  ```bash
  rake set_env[http://uat.com]
  ```

### Coding
* edit code under `www/`
* `rake -T` to see available tasks. Frequent tasks might be: 

  ```bash
  rake ios:build         # run platform/ios/cordova/build
  rake ios:run           # run platform/ios/cordova/run
  rake android:build     # run platform/android/cordova/build
  rake android:run       # run platform/android/cordova/run
  rake jasmine:headless  # Run Jasmine specs headlessly
  ```

