# quick_depth_handeye_calibration
Usually, we solve calibration problem by AX=XB.Acutally, this is too trouble with many steps. This repository introduces a quite simple but efficient method for handeye calibration with a quite high precision.


you can run:
calibrationinteractive.launch
 ![image](https://github.com/pyni/quick_depth_handeye_calibration/blob/main/img/Screenshot%20from%202021-04-08%2016-08-20.png) 
And move point cloud on the model,like this:
 ![image](https://github.com/pyni/quick_depth_handeye_calibration/blob/main/img/Screenshot%20from%202021-04-08%2016-08-37.png) 


Although it is simple, the final test precision is higher than traditional calibration methods:
 ![image](https://github.com/pyni/quick_depth_handeye_calibration/blob/main/img/Screenshot%20from%202021-04-08%2016-07-57.png) 


If anyone wants to change the initial pose, you can change it over here:
 ![image](https://github.com/pyni/quick_depth_handeye_calibration_without_calibration_board/blob/main/img/Screenshot%20from%202021-04-13%2015-34-38.png) 




本项目可以自由添加多个需要调节的link，只需要在roslaunch里面增加相应的node即可，但ns命名需要不一样，比如这个：


  <node name="itf" pkg="rviz_interactive_tf" type="interactive_tf" ns="itf2">
    <param name="parent_frame" value="/ee_link"/>
    <param name="frame" value="/camera_link2"/>
  </node>
