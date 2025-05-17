# CSE211s Final Project: RTC and ADC Display on NUCLEO-F401RE

This project is the final assignment for the **CSE211s Introduction to Embedded Systems** course at **Ain Shams University Faculty of Engineering, Department of Mechatronics** (Spring 2025). It implements a combined Real-Time Clock (RTC) and Analog-to-Digital Converter (ADC) voltage display system using an ST NUCLEO-F401RE development board and an Arduino Multifunction Shield.

The system utilizes the 4-digit 7-segment display on the shield to show either elapsed time (minutes and seconds) or the instantaneous voltage read from the onboard potentiometer via the NUCLEO's ADC.

The application logic is built using the Mbed OS framework.

**Application functionality**

The project implements the following features:

Real-Time Clock (RTC): The 7-segment display shows elapsed time in MMSS format (MinutesSeconds), starting from 0000 after a board reset.

Timer Reset (S1): Pressing the S1 button on the shield resets the elapsed time to 0000.

ADC Voltage Display (S3): Pressing and holding the S3 button on the shield reads the analog voltage from the potentiometer (connected to pin A0 on the shield/NUCLEO) using the onboard ADC. This voltage is then displayed on the 7-segment in X.XX format (e.g., 2.75).

Mode Switching: Releasing the S3 button switches the display back to showing the elapsed time. The RTC continues to increment in the background even when the voltage is displayed.

Min/Max Voltage Tracking: The system also tracks the minimum and maximum voltage values read from the potentiometer since the last reset (though these are not explicitly displayed in the standard mode according to the code provided, they are calculated).

The main() function handles the main loop, checking button states, reading the ADC, updating internal time variables, and refreshing the 7-segment display based on the current mode. A Ticker is used to increment the time every second in a separate context. The 7-segment display is driven using a shift register.

**Hardware Requirements**

ST NUCLEO-F401RE Development Board

Arduino Multifunction Shield

**Building and running**

1- Connect the Arduino Multifunction Shield to the NUCLEO-F401RE board.

2- Connect the NUCLEO board to your computer via USB.

3- Use your preferred Mbed OS build tool (Mbed CLI, Mbed Studio, etc.) to build the project for the NUCLEO_F401RE target and your chosen toolchain (e.g., ARMC6, GCC_ARM).


  $ mbed compile -m NUCLEO_F401RE -t <TOOLCHAIN> --flash

Replace <TOOLCHAIN> with your toolchain (e.g., ARMC6). The --flash flag will automatically program the board after a successful build.

4- Alternatively, you can manually copy the generated .bin or .hex file from the BUILD directory to the NUCLEO board's virtual drive.

5- Press the black reset button on the NUCLEO board to run the application.

**Expected behavior**

Upon reset, the display should show 0000 and begin counting up: 0001, 0002, ... 0059, 0100, etc.

Pressing S1 should reset the display to 0000.

Pressing and holding S3 should show the potentiometer voltage (e.g., 3.30, 1.65, 0.00). The value should change as you rotate the potentiometer knob.

Releasing S3 should make the display return to showing the elapsed time from where it left off.

**Video Demonstration**

A video showcasing the project's functionality, including the RTC counting, resetting the timer with S1, and displaying the voltage with S3, is available via the following Google Drive link:

(https://drive.google.com/file/d/1OPm_c9VCSLpj6Hjp9WXttaztiF4Snf8j/view?usp=sharing)

**Contributors**

AHMED IBRAHIM [2101122]

MOHAMED TAREK [2100287]

OMAR MAGDY [2100273]
