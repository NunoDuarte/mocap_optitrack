# Optitrack at LASA or IST

This package streams ROS pose data (pose messages and TF frames) for detected
optitrack rigid bodies.

NOTE: It is compatible with *both* the new and old versions of the Motive
software. However following instructions are **running in
version (Motive 2.2)**.

It is a fork of the
[ros-drivers](https://github.com/epfl-lasa/mocap_optitrack) package, with
minor modifications (primarily in the configuration options).

## Quick launch at EPFL

    roslaunch mocap_optitrack epfl_optitrack.launch
    
## Quick launch at IST

    roslaunch mocap_optitrack mocap.launch

## Configuration options

By default, this node only streams pose data for rigid body IDs listed in the
[epfl.yaml](https://github.com/NunoDuarte/mocap_optitrack/blob/master/config/epfl.yaml) or [mocap.yaml](https://github.com/NunoDuarte/mocap_optitrack/blob/master/config/mocap.yaml)
configuration files.  Edit the rigid_bodies configuration in this file (standard
yaml syntax) to provide the list of marker IDs (usually integers) that you want
to track. For each marker, you should specify the pose topics, and the name of
the TF frame (`child_frame_id`).

## Tips and tricks

You can view which frames are being published using the command: `rosrun tf tf_monitor`.

You can view a graph of the frames (to visualize parent/child frames) using the command:
`rosrun tf view_frames && evince frames.pdf`.

Lastly, `rviz` is another good option to see the frames.

See the [tf tutorial](http://wiki.ros.org/tf/Tutorials) for lots more information.
