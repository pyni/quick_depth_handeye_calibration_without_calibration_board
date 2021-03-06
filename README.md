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
注意，如果是多相机的化这里的calibration.world里面的frameName和pointCloudTopicName等等都需要换个名字。具体而言，我们这边其实把world这部分提供在这里了，也就是added.world，对于任意机器人，只要在其本身的world里面把我们这个added.world加进去就行：
![Screenshot from 2021-05-28 21-03-14](https://user-images.githubusercontent.com/18031767/120055094-778f2880-c066-11eb-93e6-b1b6ddb8037c.png)
还有一个需要注意的是，gazebo建模里面，也就是world里面相机的link并不会发布，所以，这里需要额外发布link。所以，我们这边写了一个程序，专门将这些点云进行发布，同时进行拼接,下面蓝色部分即为点云部分:
![Screenshot from 2021-05-29 11-44-36](https://user-images.githubusercontent.com/18031767/120057130-60a30300-c073-11eb-8135-19975e18000b.png)
(最近忙，这部分毕业后再写)
