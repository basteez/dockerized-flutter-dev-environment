# Dockerized Flutter Dev Environment

This is a fully functional Flutter development environment packaged in a Docker container.

## Prerequisites
* Docker must be installed on your machine
* VSCode with the [Remote Development Extension Pack](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack)

## How to use it
1. Click on the Remote "Quick Access" status bar item ![](https://microsoft.github.io/vscode-remote-release/images/remote-dev-status-bar.png)
2. Click on "Open folder in container..."
3. Select the folder that includes the Dockerfile
4. Wait for the container to be created (it may take a while, depending on your machine's power and your internet speed)
5. Once the container is running, open a terminal inside VSCode and run `flutter doctor`, you should see that everything is ok but a couple of warning/errors about Chrome, Android Studio and connected devices. You can skip the first two, we're going to fix the latter in a while.
6. Move into the workspace folder and start creating your flutter projects with `flutter create <your_project_name>`

## You don't need an android usb connected device
I don't know if it's possible to do something similar with an iOS device, but if you own an android device you can run and debug your project remotely via wi-fi connection:
1. Make sure your computer and your device are on the same wi-fi network
2. Make sure your device has developer tools and usb debugging enabled (yes, it's needed although we're going to use wi-fi)
3. Inside the container, open a terminal and run `adb connect <your_device_ip_address>:5555`

That's all! Now if you run `adb devices` you should see your phonw/tablet connected and from now on you can simply run `flutter run` from the project directory inside the container's workspace directory and after a while the app should open on your device.