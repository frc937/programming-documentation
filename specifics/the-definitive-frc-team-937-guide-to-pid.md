---
description: 'WORK IN PROGRESS: How To PID'
---

# The Definitive FRC Team 937 Guide to PID

{% hint style="danger" %}
## THIS IS A WORK IN PROGRESS. ANYTHING AND EVERYTHING IT CURRENTLY SAYS COULD BE WRONG. WE WILL UPDATE IT AS WE LEARN MORE.
{% endhint %}

We're hoping to learn more about PID over the next year or so. As we do, this guide will grow and mature. For now, here's a bunch of links that help explain How To PID.

PID control is really complicated, but at a basic level it's a form of closed-loop control, so it uses a feedback sensor (for our purposes, almost always an encoder) to quickly and efficiently move to and maintain a set velocity or position, known as the setpoint. It uses a number of gains, namely Proportional gain, Integral gain, Derivative gain, and nowadays usually a feedforward. This is where the name PID comes from - Proportional, Integral, and Derivative.

This explains the basic concept behind a PID controller:

{% embed url="https://pidexplained.com/pid-controller-explained" %}

WPILib documentation for PID:

{% hint style="info" %}
In ALMOST ALL CASES, we DO NOT use WPILib classes for PID. Instead, we use the built-in PID support on our motor controllers, since they are generally more advanced, easier to use, and have a much faster referesh rate.

Therefore, this documentation is useful for matters of principle, but most of its code examples aren't super helpful for us.
{% endhint %}

{% embed url="https://docs.wpilib.org/en/stable/docs/software/advanced-controls/introduction/introduction-to-pid.html" %}

A little more basic-overview type stuff about PID control on FRC bots:

{% embed url="https://frc-pdr.readthedocs.io/en/latest/control/pid_control.html" %}

A Chief Delphi post that discusses velocity tuning with Talon SRXs:

{% embed url="https://www.chiefdelphi.com/t/talon-srx-pidf-velocity-tuning/402112" %}

A Chief Delphi post that discusses position tuning with Talon SRXs:

{% embed url="https://www.chiefdelphi.com/t/talon-srx-position-control/377523" %}

Information about tuning velocity PID on a SPARK MAX, specifically for a shooter:

{% hint style="info" %}
**Note for 2022 Cow Town**

This will be VERY useful for tuning the flywheel on OwOange Juice
{% endhint %}

{% embed url="https://www.chiefdelphi.com/t/tune-rev-spark-max-pid-for-shooter/379068" %}

Information about how to tune a flywheel such that it will change speed based off of the distance from the target reported by the Limelight (our computer vision camera), as opposed to running the flywheel at a set speed and physically moving the bot.

{% embed url="https://ranashreyas.medium.com/flywheel-shooter-software-for-frc-b51b951e45c3" %}

A lovely Github project made by Team 2930 Sonic Squirrels that makes it easy to tune a PID loop for a shooter:

{% hint style="info" %}
Side note: we haven't personally tested this project
{% endhint %}

{% embed url="https://github.com/FRC-Sonic-Squirrels/Flywheel-Tuner/tree/2022-CTRE" %}
