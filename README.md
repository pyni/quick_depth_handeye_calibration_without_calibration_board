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
 
   ![image]( https://github.com/pyni/quick_depth_handeye_calibration_without_calibration_board/blob/main/img/Screenshot%20from%202021-04-14%2021-00-52.png) 


Improvement:
The method above 


第三类方法（通过gazebo进行点云建模，然后再进行icp标定）：
gazebo建模方法（这里用的是iiwa的，本质就是搭建几个gazebo的kinect拼接即可）gazebo的环境导出来可以来替换calibration.world
注意，如果是多相机的化这里的calibration.world里面的frameName和pointCloudTopicName等等都需要换个名字
还有一个需要注意的是，gazebo建模里面，也就是world里面相机的link并不会发布，所以，这里需要额外发布link：

