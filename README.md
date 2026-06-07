# ROS2-NO-PUBKEY-SOLUTION
IF YOU ARE ALSO FACING NO-PUBKEY ERROR WHILE ADDING ROS2 Repo from ORIGINAL SOURCE and from official website commands, THEN FIX THEM.

1) Removed ros2.list from below location if it was already present.

/etc/apt/sources.list.d/ros2.list
2) Downloaded key via $ curl http://repo.ros2.org/repos.key | sudo apt-key add -. Reference post : https://answers.ros.org/question/379190/apt-update-signatures-were-invalid-f42ed6fbab17c654/

3) You will get a key added similar to /etc/apt/trusted.gpg But name could vary. You can find name of key by sudo apt-key list

4) copy the file /etc/apt/trusted.gpg to location /usr/share/keyrings and rename it to ros-archive-keyring.gpg

5) If you were following ros2 humble installation steps (https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debians.html), you might have realized that below command is adding echo
<code>
deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null </code>

This Above Command line will add active & latest link to apt source - deb [arch=arm64 signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu jammy main to the file /etc/apt/sources.list.d/ros2.list

8) Now, following the remaining steps in installation tutorial should help you to get humble installed.
