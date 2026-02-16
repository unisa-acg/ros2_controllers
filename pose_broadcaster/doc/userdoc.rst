:github_url: https://github.com/ros-controls/ros2_controllers/blob/{REPOS_FILE_BRANCH}/pose_broadcaster/doc/userdoc.rst

.. _pose_broadcaster_userdoc:

Pose Broadcaster
--------------------------------
Broadcaster for poses measured by a robot or a sensor.
Poses are published as ``geometry_msgs/msg/PoseStamped`` messages and optionally as tf transforms.

The controller is a wrapper around the ``PoseSensor`` semantic component (see ``controller_interface`` package).

Parameters
^^^^^^^^^^^
This controller uses the `generate_parameter_library <https://github.com/PickNikRobotics/generate_parameter_library>`_ to handle its parameters. The parameter `definition file located in the src folder <https://github.com/ros-controls/ros2_controllers/blob/{REPOS_FILE_BRANCH}/pose_broadcaster/src/pose_broadcaster_parameters.yaml>`_ contains descriptions for all the parameters used by the controller.

List of parameters
=========================
.. generate_parameter_library_details:: ../src/pose_broadcaster_parameters.yaml


An example parameter file
=========================

An example parameter file for this controller can be found in `the test directory <https://github.com/ros-controls/ros2_controllers/blob/{REPOS_FILE_BRANCH}/pose_broadcaster/test/pose_broadcaster_params.yaml>`_:

.. literalinclude:: ../test/pose_broadcaster_params.yaml
   :language: yaml

QoS Configuration
=========================

The pose broadcaster supports two Quality of Service (QoS) profiles for the pose publisher:

* **reliable** (default): Uses ``SystemDefaultsQoS`` - Guaranteed message delivery, keep_last 10, volatile
* **best_effort**: Uses ``SensorDataQoS`` - Faster but may lose messages, keep_last 5, volatile

Example with best_effort QoS:

.. literalinclude:: ../test/pose_broadcaster_custom_qos_params.yaml
   :language: yaml

Choose **reliable** for critical pose data that must not be lost, or **best_effort** for high-frequency sensor data where missing occasional messages is acceptable.
