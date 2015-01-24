# Precompiled Ardupilot SITL package

A package containing Linux binaries for the Ardupilot software-in-the-loop (SITL) simulator, for easy deployment to a Linux desktop or an Amazon EC2 instance.

The binaries were compiled on Ubuntu 14.04 from the [ardupilot master branch](https://github.com/diydrones/ardupilot) on the date noted in the filename, rather than a release branch, in order to obtain a working binary for both ArduCopter and APMrover2. They have been tested on Amazon's default Linux instance.

This package includes a GPLv3 license, as it is derived from the [Ardupilot](https://github.com/diydrones/ardupilot) project.

### Getting started

Simply unpack the tarball in any convenient location, change into the vehicle directory, and run the desired script.

All simulator scripts from the Ardupilot project are included.

In addition, a script called `sim_only.sh` has been provided to run the simulator alone without MAVProxy.

```bash
$ tar xvfz sitl-20150123.tgz
$ cd sitl/ArduCopter      # or APMrover2 for the ground rover
$ ../Tools/autotest/sim_only.sh
```

### EC2 instance

To run SITL on an EC2 instance, copy the contents of the file `ec2-user-data.txt` to the User Data field when you launch a new instance.

This will cause EC2 to install the SITL package and its prerequisites in the right places.

> NOTE: After you launch the instance, you must immediately reboot it to force SITL to start up correctly. For some reason, SITL won't start properly from cloud-init, but will start from rc.local.

