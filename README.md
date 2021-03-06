SparkFun Low-Power Machine Learning Examples
============================================

<p align="center" valign="middle">
   <img src="https://cdn.sparkfun.com/assets/custom_pages/3/3/4/dark-logo-red-flame.png"  width=200>  
   <img src="https://www.gstatic.com/devrel-devsite/prod/v0ee3aab4746d30f0d189bec7de9a20f1b6a1e49e000167a7abfdd73e499fffdc/tensorflow/images/lockup.svg"  width=300>   
</p>

<img src="https://cdn.sparkfun.com//assets/parts/1/3/5/6/7/15170-SparkFun_Edge_Development_Board_-_Apollo3_Blue-01a.jpg"  align="right" width=300> 

This repository contains examples that demonstrate the use of [TensorFlow Lite](https://www.tensorflow.org/lite/) based machine learning executing on the [SparkFun Edge Development](https://www.sparkfun.com/products/15170) board. The examples are designed for use within the Arduino development environment, enabling rapid setup and deployment of the examples.

The examples contained in this repository make use of the variety of sensors available on the SparkFun Edge Development board to show the modern capabilities of machine learning executing on a low-power microcontroller-based system.

The following examples are included in the repository:
* micro_speech - Using the on-board microphone to detect a spoken keyword
* person_detection - Using an attached camera to detect the presence of a person in an image. 
* magic_wand - Using the on-board accelerometer to detect gestures (movement of the breakout board) 

## Contents

* [Required Hardware ](#required-hardware)
* [Software Setup](#software-setup)
* [Running an Example](#running-an-example)

Required Hardware
-----------------

To run the examples, the following hardware is required:
* [SparkFun Edge Development breakout board](https://www.sparkfun.com/products/15170)
* [Himax CMOS Imaging Camera – HM01B0](https://www.sparkfun.com/products/15570)
* [SparkFun Serial Basic Breakout](https://www.sparkfun.com/products/14050) or [SparkFun Serial Basic Breakout USB-C](https://www.sparkfun.com/products/15096)
* [USB-A to micro-B cable](https://www.sparkfun.com/products/10215) or a cable to connect the Serial Basic to the development computer.

<p align="center" valign="middle">
   <img src="https://cdn.sparkfun.com//assets/parts/1/3/5/6/7/15170-SparkFun_Edge_Development_Board_-_Apollo3_Blue-01a.jpg"  width=80>  
   <img src="https://cdn.sparkfun.com//assets/parts/1/4/1/6/5/15570-Himax_Imaging_Camera-01.jpg"  width=80>   
   <img src="https://cdn.sparkfun.com//assets/parts/1/1/8/8/8/14050-01.jpg"  width=80>
   <img src="https://cdn.sparkfun.com//assets/parts/4/5/5/8/10215-01.jpg"  width=80>  
</p>

Software Setup
--------------
The examples in this repository are for use and execution within the Arduino development environment. This section details the steps required to setup Arduino for the examples.

### Install Arduino

<img src="https://www.arduino.cc/en/pub/skins/arduinoWide/img/ArduinoAPP-01.svg"  align="left" width=40>

Arduino is avilable for a variety of platforms. To ensure compatiblity with the demos in this repository, the latest version should be installed.

The Arduino application is available for a variety of platforms and is available online from Arduino. Download the application from the Arduino website using this [link](https://www.arduino.cc/en/Main/Software).

### Install the TensorFlowLite Library

The examples utilize the TensorFlowLight Arduino libary, which is installed using the Arduino Library Manager. 

To install this library, use the following steps:
<img src="resource/TFL_Install.png"  align="right" width=350>
* In Arduino, select the "Manage Libraries..." menu item. ***Tools > Manage Libraries...***
* In the Library Manager interface, search for tensorflow
* Select the library **Arduino_TensorFlowLite** by **TensorFlow Authors**
* Select the *non-precompiled* version of the libary
* Select the **Install** button to install the library

### Install the Himax HM01B0 Camera Library

With the Library Manager dialog still displayed, install the Himax camera driver.
* Search for ***himax***
* Select the **SparkFun Himax HM01B0 Camera"** Library and then select the **Install** button.  

Once the install is completed, close the Arduino *Library Manager* dialog.

### Install the SparkFun Boards Package

Load the SparkFun Boards package into the Arduino Board Manger.

To install package, use the following steps:

* In Arduino, open the Preferences menu item. ***File > Preferences***, (macOS) ***Arduino > Preferences***
* Add the following path to the ***Additional Boards Manager URLs:*** path in preferences.

  ```https://raw.githubusercontent.com/sparkfun/Arduino_Boards/master/IDE_Board_Manager/package_sparkfun_index.json```

* Select the ***OK*** button to save the preferences.

<img src="resource/BoardPacakgeURL.png" >

#### Install the SparkFun Artemis Boards Package 

Once the location of the SparkFun boards package is set in the preferences, the board definition package for the SparkFun Apollo3 boards must be installed. 

To install package, use the following steps:
<img src="resource/BoardManager.png"  align="right" width=350>
* In Arduino, open the Preferences menu item. ***Tools > Board "..." > Manage Boards...***
* Search for *SparkFun*
* Select the **SparkFun Apollo3 Boards" package (use v1.0.24 or later)
* Close the dialog
* Select the SparkFun Edge Board. ***Tools > Boards "..." > SparkFun Edge***
* Set the Bootloader to the ***SparkFun Variable Loader***. ***Tools > Bootloader "..." > SparkFun Variable Loader..."

Running an Example
------------------

### Configure the Hardware
* If this is a camera example, make sure the camera is installed on the Edge board.
* Plug USB cable into computer
* Connect Serial to USB adapter to USB cable
* Plug in Edge board to adpater


### Configure the Software
* Install and setup Arduino as described [above](#software-setup).
* Download (or clone) this repo to favorite location
* Open Arduino
* Open an example from this repo through Arduino by clicking on a ```.ino``` file in one of the example directories
  * ```micro_speech```
* Select the ```SparkFun Edge``` board (Tools->Board under 'SparkFun Apollo3')
* Select the proper port to connect with the baord (Tools->Port)
  * Windows - COM Port
  * Linux - /dev/ttyUSB*, where * is a number. NOTE: Permissions on this device needs to include user read and write (chmod 666)
  * macOS - /dev/cu.usbserial* 
* Change the **Bootloader** from *Ambiq Secure Bootloader (Default)* to *SparkFun Variable Loader (Enable w/ Artemis Bootloader)* (Tools->Bootloader)
  * (Your boards have received the upgraded bootloader already)
* Change the ```SVL Baud Rate``` from *921600* to *460800*

### Upload
* Compile with the ```Verify``` button (checkmark symbol)
* Upload with the ```Upload``` button (arrow symbol)
  * If uploading fails try lowering the bootloader baud rate
* Note: You will see some warnings from the compiler, these can be ignored.
* Note: The bootloader attempts to upload for 3 times. If all three attempts fail, try adjusting the baud rate. 

### Serial Monitor
* Open the Serial Monitor by clicking on the magnifying glass icon (top right) or (Tools->Serial Monitor)

## Training a Speech Model
The micro speech example has a model that is trained to recognize "Yes" and "No". An example of how to train a new model based on Google collected sample phrases is included in the tensorflow micro_speech example repository. The method listed utilizes Google Colaboratory to run the training session - an Jypter notebooks based system that presents a Python based notebook and abstracts the management of compute resources.

The notebook to run the training for this example is contained in the tensorflow github repository at this [location.](https://github.com/tensorflow/tensorflow/blob/master/tensorflow/lite/experimental/micro/examples/micro_speech/train_speech_model.ipynb)

