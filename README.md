# SIDFLC (Smartphone Interfaced Device For Launching Coins)

<img src="https://github.com/ElectronicSpaceCat/SIDFLC/blob/master/extra/images/device.jpg" width="250"> <img src="https://github.com/ElectronicSpaceCat/SIDFLC/blob/master/extra/images/device_on_phone.jpg" width="250"> <img src="https://github.com/ElectronicSpaceCat/SIDFLC/blob/master/extra/images/DSC_0491.JPG" width="250">

The SIDFLC is an over-engineered proof-of-concept projectile launcher with the intention of being as small as possible yet delivering a decent target range. It is designed to sit at the back of a mobile phone where the user physically pulls and releases the projectile-carriage to launch. It uses torsion springs instead of rubberbands (which you'll see in most designs). It can reach about 15 feet with the current springs, but it can easily hit 20-25 feet with larger ones. It can typically hit within 1 to 5 inches of the target if tuned and calibrated well. The big difference with SIDFLC is that it has two custom circuit boards working together to read the projectile-carriage positon and device height using time-of-flight (ToF) sensors. The sensor data is relayed over bluetooth low energy (BLE) to the mobile phone. The mobile's gyroscope is required in conjuntion with the sensor data for target alignment and ballistic calculations. It runs on a 3.7V lithium-ion battery which can be charged over USB-C and a single button is used to turn on/off the device. To top it off, the device has over-the-air (OTA) device-firmeware-update (DFU) where it can recieve updates over Bluetooth via the Android mobile application.

<img src="https://github.com/ElectronicSpaceCat/SIDFLC/blob/master/extra/images/DSC_0487.JPG" width="200"> <img src="https://github.com/ElectronicSpaceCat/SIDFLC/blob/master/extra/images/device_model.png" width="500">

### Device Features
* Dimensions: 95mm x 62mm x 8mm
* Easy spring swap out (take caution when doing so)
* USB-C battery charging
* Single button interface: - on/off, force off, delete bonds, bootloader
* Indication LED 1 - System running, bootloader, Bluetooth advertising
* Indication LED 2 - Charge status

## Android App (currently not avaiable for download)

<img src="https://github.com/ElectronicSpaceCat/SIDFLC/blob/master/extra/images/Screenshot_20230917-120730.png" width="150"> <img src="https://github.com/ElectronicSpaceCat/SIDFLC/blob/master/extra/images/Screenshot_20230217-104148.png" width="150"> <img src="https://github.com/ElectronicSpaceCat/SIDFLC/blob/master/extra/images/Screenshot_20230217-104220.png" width="150"> <img src="https://github.com/ElectronicSpaceCat/SIDFLC/blob/master/extra/images/Screenshot_20230217-104228.png" width="150"> <img src="https://github.com/ElectronicSpaceCat/SIDFLC/blob/master/extra/images/Screenshot_20230217-104358.png" width="150"> <img src="https://github.com/ElectronicSpaceCat/SIDFLC/blob/master/extra/images/Screenshot_20230217-104308.png" width="150">

### App Features
* OTA-DFU
* Assisted target alignment
* Assisted ballistics calculations
* Auto ToF sensor calibration
* ToF sensor tuner (advanced)
* Auto bluetooth bonding
* Gyroscope calibration
* Projectile editor
* Unit selector
* Battery status indicator
* Charging indicator
* Can be used as a level
* Can be used as a range finder (when connected to device)

## How it works
In order to calculate the projectile ballistics, the device height, target distance, and target height are required in sequence. The device height is obtained by using one of the device's ToF sensors to aim at the ground and the target distance and height are obtained by utilizing the phone's pitch angle from the gyro. When all three parameters are locked in, the app then uses the second ToF sensor in the device to translate the position of the projectile-carriage to a deflection angle of the springs relative to their default position in the device. The deflection angle is then ran through algorythms to find the exit velocity of the projectile. Finally a ballistics analysis of the projectile is done to find an estimated impact distance and height.

**Application Instructions:**
* Press **Device Height (DH)** button to get the height while using the app to assist in aligning the phone virtically.
* Press **Target Distance (TD)** button for target distance while aiming the center dot at the base of the target.
* Press **Target Height (TH)** button for target height and move the center dot from the base up to the target.
* Use your index finger to pull down the projectile-carriage to build stored energy in the springs.
* Use the virtical line on the screen as a guide to keep the target centered.
* The carriage posistion and angle of the phone will continuously upate the hit-confidence indicator.
* Release the carriage when the indicator is close to 100%

  **NOTES:**
  * The ballistics calculations assumes one is standing on flat ground.
  * **DH**, **TD**, and **TH** can be set to **Auto** or **Manual** entry mode which is indicated by an **A** or **M** under each button. **Auto** lets the app continuously caluculate the value until locked in, while **Manual** is manually entered. The manual mode is handy if the device is at a fixed position or target data is known.
  * A geen check mark under a button indicates the parameter data has been locked in, a red X indicates it is pending. When all parameters are aquired, it will switch to targeting mode.
  * The lock icon under a button has three states: **Unlocked**, **Locked** , and **Not Availabe**. The **Locked** and **Unlocked** states are associated with auto modes for **TD** and **TH**. Locked status means that once the parameter is acquired in **Auto** mode, it is locked in and will be ignored when resetting target data. An example is if one would like to use the auto calculation to acquire **TH** but do not want to recalculate it when target data has been reset for an new sequence.
  * The **TH** can be manually set to zero if the target is flat and at ground level.
  * When **DH**, **TD**, or **TH** are set manually, they will be skipped during the target data acquisition sequence. 

A pictorial for how to use it:  
<img src="https://github.com/ElectronicSpaceCat/SIDFLC/blob/master/extra/images/instructions.png" width="400">

## Mobile Phone Attachment
Ideally, something like the FLEXclip could be used to fix the device to the back of a mobile phone, eliminating the need for a custom case: https://www.synergywiz.com/flexclip

## Project Contents
* Android app: https://github.com/ElectronicSpaceCat/sidflc-android-app
* Firmware: https://github.com/ElectronicSpaceCat/sidflc-fw-app
* Bootloader: https://github.com/ElectronicSpaceCat/sidflc-fw-bootloader
* PCB primary: https://github.com/ElectronicSpaceCat/sidflc-pcb-bt
* PCB secondary: https://github.com/ElectronicSpaceCat/sidflc-pcb-tof
* CAD model: https://github.com/ElectronicSpaceCat/sidflc-3d-model
