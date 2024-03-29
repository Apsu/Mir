# Mir

Mir is a highly-symmetric, differentially-actuated, fully-parallel, 3-axis 3D printer design.

![mockup](Mockup.png)

## Overview

This design has the following major features:

### Symmetric

Mir is symmetric within each axis, as well as across the XY gantry, and has other symmetries between combinations of sections.

The amount and variety of mirrored symmetries in this design is why the codename is 'Mir'.

### Fully Parallel

Mir has fixed motors and a fixed bed. The moving portions are driven entirely in parallel, without one axis moving the motors for another axis.

Parallel kinematic systems are less prone to accumulated error than serial systems where actuators are chained together, each moving the position of the next in the chain.

In 3D printers, having a fixed bed is also a benefit due to beds generally being the heaviest part to move. In addition, a bed changes its inertia as the piece progresses in being printed, due to the changing mass attached to the bed.

### Differential Actuation

The arrangement of actuators in this design can be seen as a pair of H-bot 2-axis differential units, each unit 90 degrees (orthogonal) from the other, and each containing two motors. These H-bot units control a vertical (Z) and horizontal (X or Y) axis.

![hbot](HbotDiagram.png)

The units are split in half, with each half placed apart from each other across the center of the frame, containing one motor, and connect together via a rigid cross piece. When split this way, you get a T-shaped belt arrangement in each half-unit, each a mirror of its corresponding half.

![half](HalfDiagram.png)

![mirrorhalf](MirroredHalfDiagram.png)

Driving a half-unit motor will result in diagonal movement of its carriage, moving both vertically and horizontally. Driving the other half-unit motor the same way will result in a diagonal movement that adds vertically but subtracts -- and therefore cancels the first unit's motion -- horizontally, due to the rigid cross connection. 

![zpair](ZPairBeltPath.png)

Driving the paired motors in opposite directions will cancel vertically and add horizontally.

![xpair](XPairBeltPath.png)

The result is that the system provides differential control of vertical and horizontal axes in parallel, giving full XYZ parallel motion.

### Torque Cancellation

Net vertical motion results in torques that are balanced and cancelled in a novel way, as follows:

Because the half-units have mirrored belting in their horizontal axis, and because the differential actuation cancels their horizontal forces across the frame, this results in a net torque around the vertical axis from that pair of half-units.

![horiztorque](HorizontalTorque.png)

The direction of the net torque depends on which side of the horizontal belt the carriages are attached to. If one pair uses top belt attachment and the other uses bottom belt attachment, the net torques will themselves cancel across the center as well, for net vertical motion.

![horiztorquecancel](HorizontalTorqueCancel.png)

Horizontal motion in one axis operates via cancellation across opposite pairs of vertical carriages, which results in a torque around the other horizontal axis. This torque is applied through the cross-gantry pieces, and since their carriages are rigid attachment points, and belt loops provide good static tension, net torque is significantly reduced.

This is difficult to represent visually but the following diagram may help.

![verticaltorquecancel](VerticalTorqueCancel.png)

### Belt-Driven

Each actuator uses a belt path with only 90 and 180 degree turns, and no twists or parallel belting/stacked pulleys. Belt runs can be open or continuous as desired, though the reference design uses open runs, terminated on the driven carriages.

Using belts for each axis allows for smooth motion with fine resolution, flexible scaling, lighter weight, and generally higher top speeds than screws.

## Kinematics

The relationship between the mirrored differential drive units is described by the following equations:

![fkdiagram](FKDiagram.png)

Which can be represented by the following matrix transform:

![fkmatrix](ForwardKinematics.png)

And the inverse kinematics by this matrix transform:

![ikmatrix](InverseKinematics.png)