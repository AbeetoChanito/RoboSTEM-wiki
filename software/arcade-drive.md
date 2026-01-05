---
description: This section will highlight how to code different drive methods.
---

# Arcade Drive

## Arcade Drive

Arcade drive is a style of stick mapping. The concept of it is making 1 stick's horizontal axis spin the robot in place. While another stick's vertical axis controls the robots movement backward and forward. &#x20;

<figure><img src="../.gitbook/assets/Screenshot 2026-01-04 at 10.55.35 PM.png" alt="" width="369"><figcaption><p>Image from Vexcode IQ</p></figcaption></figure>

This is the standard configuration for arcade drive. It uses the D Axis of the controller (Right Horizontal) to control robot rotation. And the A axis to control forward and reverse. But this is not the only way to do arcade drive.

<div><figure><img src="../.gitbook/assets/Screenshot 2026-01-04 at 11.00.16 PM.png" alt=""><figcaption></figcaption></figure> <figure><img src="../.gitbook/assets/Screenshot 2026-01-04 at 11.00.04 PM.png" alt=""><figcaption></figcaption></figure></div>

Here are 2 examples of other ways to do split arcade. We have reversed, where the left stick controls turn and the right controls forward and backward movement and 1 stick mode where all the controls are in 1 stick without using the other stick. This allows the other stick to be used for other things such as controlling other motors.

## How to code arcade drive (Advanced)

{% code overflow="wrap" %}
```python
int whenStarted1() { # Starts this code when the program starts
  while (true) {
    RightDrive.spin(forward); # Spins the motors foward so we can control them by controlling their velocities
    LeftDrive.spin(forward);
    RightDrive.setVelocity((Controller.AxisA.position() + Controller.AxisC.position()), percent); # Sets the right drive to the foward stick location + the turn stick location
    RightDrive.setVelocity((-(Controller.AxisA.position()) - Controller.AxisC.position()), percent); # Sets the left drive to the foward stick location - the turn stick location
  wait(20, msec); # Slows down the loop a bit to speed up the brain.
  }
  return 0; 
}
```
{% endcode %}

If you want to modify this code to use a different stick layout change the controller axis in "Controller.AxisA.position" or "Controller.AxisC.position"

<figure><img src="../.gitbook/assets/Screenshot 2026-01-04 at 11.31.08 PM.png" alt=""><figcaption></figcaption></figure>

Here is the code in blocks form. This code creates a split arcade code that works for driving with the controller.

{% file src="../.gitbook/assets/Split Arcade (1).iqblocks" %}

This is a more advanced option for coding arcade drive but can be better as it lets you implement more advanced driving control letting you adjust the top speed of your robot to be more controllable along with the turning speed with some additional code.&#x20;

Here is an example of a advanced split arcade that allows the user to further adjust the handling of their robot.

```python
myVariable = 0
Fwd = 0
Turn = 0
Speed = 0
FwdSpeed = 0
TurnSpeed = 0
Left_Raw = 0
Right_Raw = 0
Max_Power = 0

def when_started1():
    global myVariable, Fwd, Turn, Speed, FwdSpeed, TurnSpeed, Left_Raw, Right_Raw, Max_Power
    FwdSpeed = 1
    # FwdSpeed, 0-1 multiplier, ex 0.8 would be 80% velo
    TurnSpeed = 1
    # TurnSpeed, 0-1 multiplier, ex 0.8 would be 80% turn velo
    RightDrive.spin(FORWARD)
    LeftDrive.spin(FORWARD)
    while True:
        Fwd = 0
        Turn = 0
        if math.fabs(controller.axisA.position()) >= 5:
            Fwd = controller.axisA.position() * FwdSpeed
        else:
            Fwd = 0
        if math.fabs(controller.axisC.position()) >= 5:
            Turn = controller.axisC.position() * TurnSpeed
        else:
            Turn = 0
        Right_Raw = Fwd - Turn
        Left_Raw = Fwd + Turn
        Max_Power = max(abs(Left_Raw), abs(Right_Raw))
        if Max_Power > 100:
            Left_Raw = (Left_Raw / Max_Power) * 100
            Right_Raw = (Right_Raw / Max_Power) * 100
        RightDrive.set_velocity(Right_Raw, PERCENT)
        LeftDrive.set_velocity(Left_Raw, PERCENT)
        wait(20, MSEC)

when_started1()
```

This code allows you to adjust the top speed and turning speed and makes turning sharper with the max power variable. Please don't just copy paste the code.

## How to code split arcade (Basic)

1.  Click the small port button on the top right that looks like a port

    <figure><img src="../.gitbook/assets/Screenshot 2026-01-04 at 11.52.50 PM.png" alt="" width="375"><figcaption></figcaption></figure>


2.  Click add device

    <figure><img src="../.gitbook/assets/Screenshot 2026-01-04 at 11.53.19 PM.png" alt="" width="188"><figcaption></figcaption></figure>
3.  Select your ports and configure your drive train

    <figure><img src="../.gitbook/assets/Screenshot 2026-01-05 at 12.05.24 AM.png" alt="" width="375"><figcaption></figcaption></figure>


4. Click add device again
5. Click add controller

<figure><img src="../.gitbook/assets/Screenshot 2026-01-05 at 12.06.33 AM.png" alt="" width="375"><figcaption></figcaption></figure>

6. Click on the joysticks until you get the stick layout you want

#### And you are done!
