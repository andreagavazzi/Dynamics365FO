.. _ubr_controllers API:

Controllers API
------------------------
The ROS API for the controllers in the ubr_controllers package.


.. _point_head_api:
point_head
~~~~~~~~~~
``point_head`` provides an action interface for pointing UBR-1's head.

Subscribed Topics
+++++++++++++++++
``point_head/goal`` (`control_msgs/PointHeadGoal <http://docs.ros.org/api/control_msgs/html/action/PointHead.html>`_)
  Target to point the head at and how fast to move the head.

``point_head/cancel`` (`actionlib_msgs/GoalID <http://docs.ros.org/api/actionlib_msgs/html/msg/GoalID.html>`_)
  A request to cancel a specific goal.

Published Topics
+++++++++++++++++
``point_head/feedback`` (`control_msgs/PointHeadFeedback <http://docs.ros.org/api/control_msgs/html/action/PointHead.html>`_)
  Empty.

``point_head/status`` (`actionlib_msgs/GoalStatusArray <http://docs.ros.org/api/actionlib_msgs/html/msg/GoalStatusArray.html>`_)
  Provides status information on goals.

``point_head/result`` (`control_msgs/PointHeadResult <http://docs.ros.org/api/control_msgs/html/action/PointHead.html>`_)
  Empty.

Parameters
++++++++++
``~stop_with_action`` (bool, default: False)
  Option to stop the controller at the completion of a goal. If false, the controller will
  the final position.


.. _base_controller_api:
base_controller
~~~~~~~~~~~~~~~
``base_controller`` provides the command interface for the UBR-1 base.

Subscribed Topics
+++++++++++++++++
``base_controller/command`` (`geometry_msgs/Twist <http://docs.ros.org/api/geometry_msgs/html/msg/Twist.html>`_)
  The standard ROS interface for controlling a mobile base.

Published Topics
+++++++++++++++++
``odom`` (`nav_msgs/Odometry <http://docs.ros.org/api/nav_msgs/html/msg/Odometry.html>`_)
  The computed odometry of the base.

Parameters
++++++++++
``~base_frame`` (string, default: "base_link")
  Name of the base frame.

``~max_acceleration_x`` (double, default: 0.5)
  Maximum forward acceleration of the UBR-1.

``~max_acceleration_r`` (double, default: 2.97044)
  Maximum angular acceleration of the UBR-1.

``~max_velocity_x`` (double, default: 1.0)
  Maximum forward velocity of the UBR-1.

``~max_velocity_r`` (double, default: 4.45566)
  Maximum angular velocity of the UBR-1.

``~odometry_frame`` (string, default: "odom")
  Name of the odometric frame, if publishing tf.

``~publish_tf`` (bool, default: True)
  Option to publish tf.

``~radians_per_meter`` (double, default: 17.497814374)
  Radian per meter of the UBR-1 base.

``~timeout`` (double, default: 0.25)
  Amount of time between commands before stopping the base.

``~track_width`` (double, default: 0.33665)
  Track width of the UBR-1. This is typically calibrated using ubr_calibration,
  and stored in the /etc/ros/<distro>/robot.launch file.


.. _follow_joint_trajectory_api:
follow_joint_trajectory
~~~~~~~~~~~~~~~~~~~~~~~
``follow_joint_trajectory`` provides a trjectory interface for the configured joints defined by the joints parameter.

Subscribed Topics
+++++++++++++++++
``~/goal`` (`control_msgs/FollowJointTrajectoryGoal <http://docs.ros.org/api/control_msgs/html/action/FollowJointTrajectory.html>`_)
  Trajectory for the listed joints to follow with path and goal tolerances.

``~/cancel`` (`actionlib_msgs/GoalID <http://docs.ros.org/api/actionlib_msgs/html/msg/GoalID.html>`_)
  A request to cancel a specific goal.

Published Topics
+++++++++++++++++
``~/feedback`` (`control_msgs/FollowJointTrajectoryFeedback <http://docs.ros.org/api/control_msgs/html/action/FollowJointTrajectory.html>`_)
  Current state, error, and goal of the trajectory.

``~/status`` (`actionlib_msgs/GoalStatusArray <http://docs.ros.org/api/actionlib_msgs/html/msg/GoalStatusArray.html>`_)
  Provides status information on goals.

``~/result`` (`control_msgs/FollowJointTrajectoryResult <http://docs.ros.org/api/control_msgs/html/action/FollowJointTrajectory.html>`_)
  Provides result of trajectory following.

Parameters
++++++++++
``~joints`` ([string], default: NONE)
  List of joint names.

``~stop_with_action`` (bool, default: False)
  Option to stop the controller at the completion of a goal. If false, the controller will
  the final position.
