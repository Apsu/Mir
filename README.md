# Mir

Mir is a differentially-actuated, fully-parallel, 3-axis 3D printer design.

## Overview

This design has the following major features:

### Fully Parallel

Mir has fixed motors and a fixed bed. The moving portions are driven entirely in parallel, without one axis moving the motors for another axis.

Parallel kinematic systems are less prone to accumulated error than serial systems where actuators are chained together, each moving the position of the next in the chain.

In 3D printers, having a fixed bed is also a benefit due to beds generally being the heaviest part to move. In addition, a bed changes its inertia as the piece progresses in being printed, due to the changing mass attached to the bed.

### Differential Actuation

The arrangement of actuators in this design can be seen as a pair of H-bot 2-axis differential units, each unit 90 degrees (orthogonal) from the other, and each containing two motors. These H-bot units control a vertical (Z) and horizontal (X or Y) axis.

The units are split in half, with each half placed apart from each other across the center of the frame, containing one motor. When split this way, you get a T-shaped belt arrangement in each half-unit, each a mirror of its corresponding half.

Driving a half-unit motor will result in diagonal movement of its carriage, moving both vertically and horizontally. Driving the other half-unit motor the same way will result in a diagonal movement that adds vertically but subtracts -- and therefore cancels -- horizontally. Driving the paired motors in opposite directions will cancel vertically and add horizontally.

The result is that the system provides differential control of vertical and horizontal axes in parallel, giving full XYZ parallel motion.

### Torque Cancellation

Because the half-units have mirrored belting in their horizontal axis, and because the differential actuation cancels their horizontal forces across the frame, this results in a net torque around the vertical axis from that pair of half-units.

The direction of the net torque depends on which side of the horizontal belt the carriages are attached to. If one pair uses top belt attachment and the other uses bottom belt attachment, the net torques will themselves cancel across the center as well, for net vertical motion.

Net horizontal motion results in cancellation across opposite pairs of vertical carriages, which results in a torque around the horizontal axes. That said, gravity and gantry stiffness helps bias the differential output towards the horizontal, so the vertical torque is comparatively smaller.

### Symmetric

Mir is symmetric within each axis, as well as across the XY gantry, and has other symmetries between combinations of sections.

### Belt-Driven

Each actuator uses a belt path with only 90 and 180 degree turns, and no twists or parallel belting/stacked pulleys. Belt runs can be open or continuous as desired, though the reference design uses open runs, terminated on the driven carriages.
