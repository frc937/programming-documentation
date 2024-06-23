---
description: How to program and flash the firmware on FRC radios
---

# Radio Programming and Flashing

Radio programming kind of sucks. More accurately, flashing radio firmware onto OpenMesh radios sucks. This page, compiled from countless hours of pain, suffering, and Googling, will attempt to summarize how to do it and what to do if it doesn't work.

## Programming vs. Flashing

First, let's clarify the difference between _programming_ a radio and _flashing_ a radio.

_Programming_ a radio is simply changing the settings on the radio. You'll do this at competition to configure the radio to connect to the field rather than our laptop.&#x20;

_Flashing_ a radio, on the other hand, is the process of taking a brand-new radio and putting FRC firmware on it so that it can be used with robots at all. This is kind of a major pain in the butt sometimes.

## Programming a Radio

If you just need to program a radio, the WPILib documentation should be sufficient. If you're doing it at comp with one of the kiosks, you basically just plug it in and push the button.

{% embed url="https://docs.wpilib.org/en/stable/docs/zero-to-robot/step-3/radio-programming.html" %}

## Flashing a Radio

Again, start with WPILib documentation:

{% embed url="https://docs.wpilib.org/en/stable/docs/zero-to-robot/step-3/radio-programming.html#open-mesh-firmware-note" %}

### Troubleshooting

You will probably run into some sort of error. If you do, try the following (depending on the error):

#### NPF Name

If you see an error about NPF name, disable ALL network adapters on the machine. This is a complicated process.

1. Follow [the WPILib directions for disabling network adapters](https://docs.wpilib.org/en/stable/docs/networking/networking-introduction/roborio-network-troubleshooting.html#disabling-network-adapters)
   * Don't disable the network adapter you're using of course
2. Go to device manager and disable all the hidden network adapters you couldn't disable from control panel
3. Also disable the Bluetooth adapter, because that will ALSO interfere
4. Try flashing again

For more info:

{% embed url="https://www.chiefdelphi.com/t/frc-radio-configuration-application-bug-error-finding-npf-device-name-for-adapter-solved/339143" %}

#### Timed Out Connecting to Bridge

This happens because in order to flash the firmware, the tool has to talk to the radio right as it's booting up. This can cause issues when you're using a POE adapter (the thing that goes to the VRM and plugs into the radio and you plug a patch cable from the laptop into) since the radio will get power and get connected to the laptop at the same time.

If you get the error, try these steps:

1. Instead of plugging the patch cable from the laptop into the POE adapter (the thing that plugs into the VRM), plug it into the port on the radio itself furthest from the power jack (the one labeled "802.3af POE")
2. Follow the [normal flashing instructions](https://docs.wpilib.org/en/stable/docs/zero-to-robot/step-3/radio-programming.html#loading-frc-firmware-to-open-mesh-radio), unplug the radio from power (the POE adapter), click "flash," plug power back in when prompted, be really careful not to brick it

For more info:

{% embed url="https://www.chiefdelphi.com/t/how-to-fix-timeout-waiting-for-radio-frc-radio-config-utility/155874" %}
