---
description: In this section we will explain what tank drive is and how to code it
---

# Tank Drive

### Tank Drive

Tank drive is another form of stick mapping. The concept of it is to have the left stick's vertical axis control the speed of the left side of the drive train and the right stick's vertical axis control the right side of the drive train.

<figure><img src="../.gitbook/assets/Screenshot 2026-01-05 at 10.00.37 PM.png" alt="" width="563"><figcaption><p>Image from codeiq.vex.com</p></figcaption></figure>

### How to code Tank Drive

{% tabs %}
{% tab title="Blocks" %}
<figure><img src="../.gitbook/assets/Screenshot 2026-01-05 at 10.12.28 PM.png" alt="Code in blocks form" width="563"><figcaption></figcaption></figure>

{% file src="../.gitbook/assets/Tank Drive.iqblocks" %}
{% endtab %}

{% tab title="Python" %}
{% code overflow="wrap" %}
```py
def when_started1():
    RightDrive.spin(FORWARD) # Spin the motors to so we can adjust the speed later with the sticks
    LeftDrive.spin(FORWARD)
    while True:
        LeftDrive.set_velocity(controller.axisA.position(), PERCENT) # Set the right drive speed to the controller axis D (Vertical Right)
        RightDrive.set_velocity(-(controller.axisD.position()), PERCENT) # Set the left drive speed to the controller axis A (Vertical Left)
        wait(20, MSEC)

when_started1() # Call our loop
```
{% endcode %}
{% endtab %}

{% tab title="C++" %}
{% code overflow="wrap" %}
```c++
int whenStarted1() {
  RightDrive.spin(forward); // Spin the motors to so we can adjust the speed later with the sticks
  LeftDrive.spin(forward);
  while (true) {
    LeftDrive.setVelocity(Controller.AxisA.position(), percent); // Set the left drive speed to the controller axis A (Vertical Left)
    RightDrive.setVelocity(-(Controller.AxisD.position()), percent); // Set the right drive speed to the controller axis D (Vertical Right)
  wait(20, msec);
  }
  return 0;
}


int main() {
  vexcodeInit();
  whenStarted1(); // Call our loop
}
```
{% endcode %}
{% endtab %}
{% endtabs %}

### Summary

Tank drive is a form of driving where each sticks vertical axis controls its side motor. It lets the driver have direct control of the motors but is harder to drive

| Pros                                                                              | Cons                                                                                                                           |
| --------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Easy to code                                                                      | Uses both joysticks so you can't use 1 of them to control other things (Not really a con as not many people use 1 stick arcade) |
| Gives you more control over your robot as you can control the motors individually | Harder to drive                                                                                                                |
