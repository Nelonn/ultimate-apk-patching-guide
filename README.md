# Ultimate APK patching guide

It will help patch any Android application. With this you can, for example, remove ads

Supports any desktop OS

## Steps

- Install apktool: [Follow this guide](https://apktool.org/docs/install/)
- Install Java at least version 8
- Create your workspace directory, example `mkdir ~/apk_patching` and `cd ~/apk_patching`
- Download [uber-apk-signer](https://github.com/patrickfav/uber-apk-signer/releases) and place into your workspace directory
- Generating keypair once:
  - Run command in your workspace `keytool -genkeypair -v -keystore keystore.jks -keyalg RSA -keysize 2048 -validity 3650 -alias app`
  - Enter keystore password: `123456`
  - Then press **Enter**/**Return** many times until this utility asks something like this `Is CN=Unknown, OU=Unknown, O=Unknown, L=Unknown, ST=Unknown, C=Unknown correct?`
  - Type here `yes`
- Put your apk file into your workspace and name it `app.apk`
- Run command in your workspace `apktool d -o app app.apk`
- Modify anything that you want in `app` directory
- Run command in your workspace `apktool b app --use-aapt2 -o app_patched.apk`
- Run command in your workspace `java -jar uber-apk-signer-1.3.0.jar -a app_patched.apk --ks keystore.jks --ksAlias app --ksKeyPass 123456 --ksPass 123456 -o output`

## License

Copyright 2024 Michael Neonov

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
