# Virtual Notepad

In place of a pen or keyboard, this project attempts to offer a new way to write that makes use of a specific tool that can detect the shapes you create with your hand in the air. When you draw a letter on the gadget, it shows on the computer screen as though you had drawn it with a pen. The Arduino Nano 33 BLE Sense, which is used in this project, uses specialized sensors such a gyroscopic sensor and an accelerometer to determine the location and motion of the hand.

## Table of contents

* [License](#license)
* [Introduction](#introduction)
* [Hardware Requirements](#hardware-requirements)
* [Installing the Sketch](#installing-the-sketch)
  * [Arduino Desktop IDE](#arduino-desktop-ide)
  * [Arduino Web Editor](#arduino-web-editor)
* [Training Gestures](#training-gestures)
* [Pretrained Model](#pretrained-model)
* [Training](#training)
* [Deployment](#deployment)
* [Contributing](#contributing)

## License

This project is licensed under the MIT License, a short and simple permissive license with conditions only requiring preservation of copyright and license notices. Licensed works, modifications and larger works may be distributed under different terms and without source code.

<p align="center"> Copyright (c) 2023 SoC Refugees. All rights reserved.</p>

## Introduction

This project demonstrates the use of machine learning to examine accelerometer and gyroscope data in order to identify motions produced by the device. It illustrates the three basic phases of a machine learning project from beginning to end:

* Collecting data: You can record gestures, annotate them, and download the results using a Bluetooth connection to a website.
* Training: How to use TensorFlow to train a model to recognize motions from your data is demonstrated in a Python notebook on the free Colab service.
* Deployment: Using TensorFlow Lite Micro and the Arduino IDE, you may upload your learned model to the Arduino board.

## Hardware Requirements

The following are required:

* Arduino Nano 33 BLE Sense Board: These can be purchased independently or as part of the [TinyML Starter Kit](https://store.arduino.cc/usa/tiny-machine-learning-kit) from Arduino or distributors. Unfortunately, other Arduinos won't work because the sensor and Bluetooth code depend on accessing the unique hardware of the Nano BLE Sense.
* MicroUSB cable. This is part of the TinyML Kit, however if your computer only has USB-C connections, you'll also need a USB-A adaptor. You should also make sure the cable is at least a c because we'll be moving the board around.
* Computer: The majority of laptops, desktop computers, or even a Raspberry Pi should work with the Arduino toolchain because it is compatible with Linux, Windows, and macOS. In order to utilize the Web Bluetooth APIs during the course, you'll also need the most recent version of the Chrome web browser.

## Installing the Sketch

You must confirm that you can use the desktop IDE or the online web editor to connect to your Arduino board and successfully load sketches onto it. Depending on whether you're using the online application or a desktop application, you'll need to take the following actions after making sure you can successfully load a basic sketch:

### Arduino Desktop IDE

You must download the most recent version of this sketch if you're using the downloadable Arduino program. The simplest method is to download and unpack a zip file, but if you know how to use git, you can also clone this repository.

Make sure the Arduino board is visible and connected to the appropriate port before opening the `virtual_notepad.ino` file in the Arduino editor. Using the main menu's Sketch --> Include Library --> Manage Libraries, you must look for the libraries that the sketch requires. We can retrieve the accelerometer and gyroscope values from the board's IMU using the [`Arduino_LSM9DS1`](https://github.com/arduino-libraries/Arduino_LSM9DS1), and you must have at least version 1.1.0. You should also search for [`ArduinoBLE`](https://www.arduino.cc/en/Reference/ArduinoBLE) and make sure you have version 1.1.3 or newer because we'll be using Bluetooth to communicate with the website.

To compile and install the sketch on your board, simply press the upload button at this point.

### Arduino Web Editor

You should be able to build a copy of the virtual notepad sketch and then press upload to install it on your board because the web editor doesn't require any library installation and will choose the most recent versions of any libraries needed.

## Training Gestures

Alphabet gestures were captured for multiple times (around 30 to 40) for each character through the Arduino's gyroscope data.

## Pretrained Model

A model that has been taught to recognize the hand-drawn alphabets A through Z is included with the sketch. Since this is based on the author's data, your results may vary. However, if you open the Serial Monitor in the Arduino IDE, you can see what the model predicts for each gesture you perform, along with an ASCII drawing of the gesture contour and a confidence score between 0 and 100.

## Training

Once you have data, you should [run the Python training notebook in Colab](https://colab.research.google.com/drive/1t4Q9yyvdGynCgU6o6ylBQ_LdEYEwvV2V) or run the `Virtual_Notepad.ipynb` and follow the steps to create and export your own model.

## Deployment

You should receive a `virtual_notepad_model_data.cc` file as a result of the Python training process. Use this version instead of the file with the same name that is in the sketch you are using. The labels and label_count variables near the top of the `virtual_notepad.ino` file should also be updated to reflect any modifications you made to the gestures you're trying to recognize.

When you upload this changed program, you should be able to use gestures and observe that your Arduino editor is recognizing them in the Serial Monitor.

## Contributing

* Fork this project by clicking the ```Fork``` button on top right corner of this page.
* Open terminal/console window.
* Clone the repository by running following command in git:

 ```bash
$ git clone https://github.com/[YOUR-USERNAME]/virtual-notepad.git
```

* Add all changes by running this command.

```bash
$ git add .
```

* Or to add specific files only, run this command.

```bash
$ git add path/to/your/file
```

* Commit changes by running these commands.

```bash
$ git commit -m "DESCRIBE YOUR CHANGES HERE"

$ git push origin
```

* Create a Pull Request by clicking the ```New pull request``` button on your repository page.

<p align="center"> Copyright (c) 2023 SoC Refugees. All rights reserved.</p>