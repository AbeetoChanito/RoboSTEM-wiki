---
description: This section will highlight how to code different drive methods.
---

# Arcade Drive

Arcade drive is a control scheme where forward/backward motion and rotation of the robot are mapped to separate, independent inputs.

## Standard Arcade Configuration

The standard configuration for arcade drive uses the y axis on the left stick to control forward/backward motion and uses the x axis on the right stick to control robot rotation.

<img src="../.gitbook/assets/Screenshot 2026-01-04 at 10.55.35 PM.png" alt="" width="369">

## Alternate Arcade Configurations
Of course, there are many other ways to configure arcade drive, too. Some examples are shown below:

<img src="../.gitbook/assets/Screenshot 2026-01-04 at 11.00.16 PM.png" width="369" alt="">

<img src="../.gitbook/assets/Screenshot 2026-01-04 at 11.00.04 PM.png" width="369" alt="">

Ultimately, which one you decide to use comes down to driver preference.



## Split Arcade Coding (Basic)


1.  Start by clicking `add a device` to add our drivetrain configuration.

<img src="../.gitbook/assets/Screenshot 2026-01-04 at 11.53.19 PM.png" alt="">

2. Select the ports that match with your drivetrain configuration.

<img src="../.gitbook/assets/Screenshot 2026-01-05 at 12.05.24 AM.png" alt="" width="375">


3. Return to the Devices menu and add a controller. Then, map the controller sticks to the drivetrain using your preferred configuration.

<figure><img src="../.gitbook/assets/Screenshot 2026-01-05 at 12.06.33 AM.png" alt="" width="375"><figcaption></figcaption></figure>


## Split Arcade Coding  (Advanced)

```c++
constexpr double throttleGain = 1.0;
constexpr double turnGain = 1.0;

int whenStarted() { // Starts this code when the program starts
  while (true) {
    RightDrive.spin(forward);
    LeftDrive.spin(forward);
    double throttle = Controller.AxisA.position() * throttleGain;
    double turn = Controller.AxisC.position() * turnGain;

    double leftPower = throttle + turn;
    double rightPower = throttle - turn;

    double maxPower = fmax(fabs(leftPower), fabs(rightPower));
    
    if (maxPower > 100) {
        leftRaw = (leftRaw / maxPower) * 100;
        rightRaw = (rightRaw / maxPower) * 100;
    }

    LeftDrive.setVelocity(leftPower, percent);
    RightDrive.setVelocity(rightPower, percent); 
    wait(20, msec)
  }
  return 0; 
}

whenStarted();
```

If you want to use a different arcade configuration, change the `throttle` and `turn` variables accordingly.