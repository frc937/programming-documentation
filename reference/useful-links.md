# Useful Links

This is a list of links to documentation and other various resources. If you're not sure how to do something, you should probably try looking here first!

## 937's GitHub

{% @github-files/github-code-block url="https://github.com/frc937" %}

* Contains code dating back to 2017
* Previous years can be referred to for help
* New repository should be made for each year
* There will eventually be a template repository for reuse every year, but it's not done yet

## WPILib Documentation

{% embed url="https://docs.wpilib.org/en/stable" %}

* Documentation for WPILib, the core library that is the base for all FRC code
  * If you don't know where to look for any given thing's documentation, it's probably here
  * Documentation for specific parts or libraries may be in other places, see below

### WPILib API Documentation

{% embed url="https://github.wpilib.org/allwpilib/docs/release/java/index.html" %}

* This is where they document the full Java API, so if you don't know what a particular method or object does, it should tell you here
* This is basically the web-accessible version of the thing that shows up when you hover over something from WPILib in VSCode
* If you don't already know what this is, **you probably don't need to worry about it**

## Phoenix Documentation

{% embed url="https://docs.ctre-phoenix.com/en/stable" %}

* Documentation for Phoenix, the framework used with all Cross The Road Electronics devices, which we use many of
* Spartronics' (team 4915) documentation for Talon SRXs:&#x20;

{% embed url="https://binnur.gitbooks.io/spartronics-developers-handbook/content/actuators/talon/programming.html" %}

### API Documentation

{% embed url="https://api.ctr-electronics.com/phoenix/release/java" %}

### \[LEGACY] Talon SRX PDF Manual

* [https://drive.google.com/file/d/14EY82vbfzq1bhJpnsjxUSxb4YQ5oGA7F/view?usp=sharing](https://drive.google.com/file/d/14EY82vbfzq1bhJpnsjxUSxb4YQ5oGA7F/view?usp=sharing)
  * **THIS. IS. OLD.** It will absolutely soon be out of date compared to Phoenix docs, if it is not already. However, it is sometimes more readable and better organized, so if you must, you can.
  * This link is restricted such that only team members can access it. This is for security reasons and to prevent the accidental spread of misinformation.

## REV Robotics Documentation

{% embed url="https://docs.revrobotics.com/docs" %}

* The root link to documentation for REV Robotics' products, which we use some of
* The documentation for each individual product will branch off of here

### SPARK MAX Documentation

{% embed url="https://docs.revrobotics.com/sparkmax" %}

* Since REV branches their documentation off in a semi-weird way, here's a link directly to the SPARK MAX documentation, which is a motor controller we use

### REVLib API Documentation

{% embed url="https://codedocs.revrobotics.com/java/index.html" %}

* Note that these are the API docs for REVLib, which (as of 2022) includes the Spark Max and the Color Sensor V3, but no other REV products
* API documentation for other REV products can be found with a Google search or from their documentation

## Limelight

{% embed url="https://docs.limelightvision.io/en/latest/index.html" %}

* The Limelight is the vision processing camera we use

### Some Helpful Examples

* Limelight implemented with a Mecanum drive, the drivetrain we use most years: [https://github.com/team581/frc-2022-rapid-react](https://github.com/team581/frc-2022-rapid-react)
  * This uses a lot of VERY advanced things that we don't use as of now (2022), such as pathfinding through a HolonomicDriveController and tracking game elements with a Limelight
    * But we could work towards these and it's parts of it do still apply to our bots
* Limelight implemented with a command-based framework, the framework we use: [https://github.com/Lambda-Corps/2020InfiniteRecharge/blob/master/src/main/java/frc/robot/commands/AlignWithVision.java](https://github.com/Lambda-Corps/2020InfiniteRecharge/blob/master/src/main/java/frc/robot/commands/AlignWithVision.java)
  * This links to the command to aim

## Mecanum Drive

{% embed url="https://mililanirobotics.gitbooks.io/frc-electrical-bible/content/Drive_Code/custom_program_mecanum_drive.html" %}

* A lovely bit of documentation written by Team 2853 that goes over how a Mecanum drivetrain works on a physical level and explains how to implement it manually, without using WPILib classes, which is important for PID
