---
description: An overview of WPILib Command-Based Programming.
---

# Command-Based Programming

## Introduction

What you just created is known as a **timed robot**. This is one of a couple of different paradigms—or ways—to organize your robot code. The other way, which is the way we use on Team 937, is a **command-based robot**.&#x20;

Command-based is a _declarative paradigm_, meaning that we declare the parts of the robot once, then use them later. It is generally made up of **commands** and **subsystems**, which we'll explain in a moment.

On Team 937, we've found that command-based code is generally better-organized and easier to extend, so we use it on all of our robots.

## Commands

Commands are the files in the robot's code that **tell** the robot what to do. This has a wide variety of applications, such as telling the robot to raise an arm, launch a catapult, or even just drive the robot.&#x20;

### The Command Scheduler

The **Command Scheduler** is the class that runs everything in the robot. Every 20 milliseconds, it goes through everything that is running, is initialized to run, or ending. (For those who know how frames in video games work—it is a very similar system). For a detailed look into the Command Scheduler, reference the WPILib documentation:

{% embed url="https://docs.wpilib.org/en/stable/docs/software/commandbased/command-scheduler.html" %}
This link contains the documentation for the WPILib Command Scheduler
{% endembed %}

The four important methods for commands are `initialize()`, `execute()`, `end()`, and `isFinished()`. For a detailed look at them, refer to:

{% embed url="https://docs.wpilib.org/en/stable/docs/software/commandbased/commands.html#initialization" %}
This link contains the documentation for WPILib Command Methods
{% endembed %}

#### Initialize

`initialize()` is run **once** when a command is **first scheduled**.&#x20;

#### Execute

`execute()` is run **continuously** while a command is scheduled. This is the primary method we use in our commands. It is useful for commands the run while a button is pressed down (i.e. spinning a wheel).

#### End

`end()` is run **once** when a command is **finished**. This is used the least of the four.

#### IsFinished

`isFinished()` is run as often as `execute()`. However, `isFinished()` returns a boolean every iteration. When it returns `true`, the command ends. If you aren't going to use this method, set it to always return `false`.&#x20;

Here is a simple command as an example, `ExtendArm.java` which we used in the 2023 season to extend the arm of Sailor Bison (our 2023 robot). This command uses activation through a button, and therefore does not use the `isFinished()` method. This command closely follows the formatting of all commands.&#x20;

{% @github-files/github-code-block url="https://github.com/frc937/robot2023/blob/cowtown2023/src/main/java/frc/robot/commands/ExtendArm.java" %}

For a detailed look into commands, refer to the WPILib documentation on commands:

{% embed url="https://docs.wpilib.org/en/stable/docs/software/commandbased/commands.html" %}
This link contains the documentation for WPILib Commands
{% endembed %}

## &#x20;Subsystems

Subsystems are used to communicate with components on the robot directly. They hide operations that can be performed on the hardware that might damage it while exposing methods that make the component easy to use.

The purpose of subsystems is to expose individual actions that the component can do and make it easy to call them, such as retracting the arm or extending it. Subsystems also hide operations that can be harmful to the robot, such as overextending the arm or keeping the arm from moving too fast.

We use subsystems to control groups of motors and hardware that make up one component, such as all the motors for the drivetrain or a motor for a flywheel.

An example subsystem is the `ArmIntake` subsystem in robot2023. This subsystem runs the intake on the arm whenever a command tells it to.

{% @github-files/github-code-block url="https://github.com/frc937/robot2023/blob/cowtown2023/src/main/java/frc/robot/subsystems/arm/ArmIntake.java" %}

{% embed url="https://docs.wpilib.org/en/stable/docs/software/commandbased/subsystems.html" %}
This link contains the documentation for WPILib Subsystems
{% endembed %}

## Binding Commands to Triggers & RobotContainer

Now that we know how to create subsystems and commands, let's look into how to actually run the commands we've made.

### RobotContainer

All the robot's subsystems, commands, and controllers are instantiated within `RobotContainer.java` (recall that instantiation means to create an instance of a class). Once we have them instantiated, we can define events that should cause different commands to run. These events are called **triggers**, and they're almost always a button being pressed on our controller.

### Triggers

There are a number of triggers that you can bind commands to, but for today, we'll just worry about button mappings, since you'll use them primarily. For this, you'll want to make sure you have an `XboxController` instantiated at the top of your `RobotContainer`.

To create a new button mapping, you'll need to do `nameOfXboxControllerObject.a().whileTrue(commandObjectToRun);`. This will run `commandObjectToRun` while the a button is held down. It will end the command as soon as the button is released. There are a few other bindings you can use (like running a command when a button is pressed, or stopping a command when a button is pressed) which you can see in the WPILib documentation:

{% embed url="https://docs.wpilib.org/en/stable/docs/software/commandbased/binding-commands-to-triggers.html" %}

For an example `RobotContainer`, see here:

{% @github-files/github-code-block url="https://github.com/frc937/robot2023/blob/0aa445ecf68107e5895de90e98247b0e143387de/src/main/java/frc/robot/RobotContainer.java" %}

## Applying Our Knowledge

Try to re-write your motor turning project from before in command-based. You'll want to create a separate, brand-new project—don't try to convert your old timed project to command-based.

All the information you need should be in the sections above on this page.

**As always, please try it on your own before you check the solution!**

### Solution

Click the link below for a repository containing the full solution:

{% @github-files/github-code-block url="https://github.com/frc937/CommandBasedSolution/tree/main/src/main/java/frc/robot" %}
