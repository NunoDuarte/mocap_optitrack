# Optitrack at LASA or IST

This package streams ROS pose data (pose messages and TF frames) for detected
optitrack rigid bodies.

NOTE: It is compatible with *both* the new and old versions of the Motive
software. However following instructions are **running in
version (Motive 2.2)**.

It is a fork of the
[ros-drivers](https://github.com/epfl-lasa/mocap_optitrack) package, with
minor modifications (primarily in the configuration options).

## Dependencies
- NatNet (v3.1.0)
- Motive (v.2.2.0 final - on Windows PC)

## Instructions
- Follow instructions to install [NatNet](https://v22.wiki.optitrack.com/index.php?title=NatNet:_Sample_Projects#Running_the_Console_Output_Sample_.28Sample_Client.29) on linux machine (Ubuntu 18.04) 
- Test that NatNet can detect Motive on Windows machine (if not, a previous step is incomplete)
- Install [Motive](https://optitrack.com/support/downloads/motive.html) on Windows PC 
- Run Motive 
- Turn on Streaming Panel (DONT FORGET: turn on Broadcast Frame - otherwise none of this is being streamed)
- Open Advanced Settings 
- Check IP address (this is IP of Windows machine)
- ping IP Address of Windows machine on linux (if you can not ping turn off Windows firewall)
- everything is set
- IF IT DOESNT WORK - try to run optitrack_yarp_stream using VS 2017 @TODO or [CodeBlocks](https://github.com/NunoDuarte/armCoupling_iCub/blob/master/lsl/pupil/README.md)

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

Check Command Port and Data Port on config file and on Motive. On Motive it should be:
- Command Port: 1510
- Data Port: 1511

On config file it should be:
- Command Port: 3110
- Data Port: 3131

why? check work of optitrack_yarp_stream. It has those values and it works. 

## Tips and tricks

You can view which frames are being published using the command: `rosrun tf tf_monitor`.

You can view a graph of the frames (to visualize parent/child frames) using the command:
`rosrun tf view_frames && evince frames.pdf`.

Lastly, `rviz` is another good option to see the frames.

See the [tf tutorial](http://wiki.ros.org/tf/Tutorials) for lots more information.
