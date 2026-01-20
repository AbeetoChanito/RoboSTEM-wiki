---
description: This section will highlight how to code tank drive.
---

# Tank Drive

## Tank Drive

Tank drive is another form of stick mapping. Each side of the drivetrain is controlled independently by its own stick.

<img src="../.gitbook/assets/Screenshot 2026-01-05 at 10.00.37 PM.png" alt="" width="563">

## Tank Coding (Basic)

<img src="../.gitbook/assets/Screenshot 2026-01-05 at 10.12.28 PM.png" alt="Code in blocks form" width="563">

## Tank Coding (Advanced)

```py
def when_started1():
    RightDrive.spin(FORWARD) # Spin the motors to so we can adjust the speed later with the sticks
    LeftDrive.spin(FORWARD)
    while True:
        LeftDrive.set_velocity(controller.axisA.position(), PERCENT) # Set the left drive speed to the controller axis A (left y)
        RightDrive.set_velocity((controller.axisD.position()), PERCENT) # Set the right drive speed to the controller axis D (right y)
        wait(20, MSEC)

when_started1() # Call our loop
```

```c++
int whenStarted1() {
  RightDrive.spin(forward); // Spin the motors to so we can adjust the speed later with the sticks
  LeftDrive.spin(forward);
  while (true) {
    LeftDrive.setVelocity(Controller.AxisA.position(), percent); // Set the left drive speed to the controller axis A (left y)
    RightDrive.setVelocity(Controller.AxisD.position(), percent); // Set the right drive speed to the controller axis D (right y)
    wait(20, msec);
  }
  return 0;
}


int main() {
  vexcodeInit();
  whenStarted1();
}
```