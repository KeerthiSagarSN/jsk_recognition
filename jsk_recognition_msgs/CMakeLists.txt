cmake_minimum_required(VERSION 3.5)
project(jsk_recognition_msgs)

# Find required packages
find_package(ament_cmake REQUIRED)
find_package(ament_cmake_python REQUIRED)
find_package(rclpy REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(std_msgs REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)
find_package(pcl_msgs REQUIRED)
find_package(builtin_interfaces REQUIRED)
#find_package(jsk_footstep_msgs REQUIRED)

# Declare ROS messages, services and actions
set(msg_files
  msg/Accuracy.msg
  msg/BoundingBoxArray.msg
  msg/BoundingBoxMovement.msg
  msg/BoundingBox.msg
  msg/BoundingBoxArrayWithCameraInfo.msg
  msg/Circle2DArray.msg
  msg/Circle2D.msg
  msg/ClassificationResult.msg
  msg/ClipResult.msg
  msg/ClusterPointIndices.msg
  msg/ColorHistogramArray.msg
  msg/ColorHistogram.msg
  msg/DepthCalibrationParameter.msg
  msg/DepthErrorResult.msg
  msg/ExifTags.msg
  msg/ExifGPSInfo.msg
  msg/HeightmapConfig.msg
  msg/Histogram.msg
  msg/HistogramWithRangeBin.msg
  msg/HistogramWithRange.msg
  msg/HistogramWithRangeArray.msg
  msg/HumanSkeleton.msg
  msg/HumanSkeletonArray.msg
  msg/ICPResult.msg
  msg/ImageDifferenceValue.msg
  msg/Int32Stamped.msg
  msg/Label.msg
  msg/LabelArray.msg
  msg/LineArray.msg
  msg/Line.msg
  msg/ModelCoefficientsArray.msg
  msg/Object.msg
  msg/ObjectArray.msg
  msg/PanoramaInfo.msg
  msg/ParallelEdgeArray.msg
  msg/ParallelEdge.msg
  msg/PlotData.msg
  msg/PointsArray.msg
  msg/PolygonArray.msg
  msg/PosedCameraInfo.msg
  msg/QueryAndProbability.msg
  msg/QuestionAndAnswerText.msg
  msg/RectArray.msg
  msg/Rect.msg
  msg/RotatedRect.msg
  msg/RotatedRectStamped.msg
  msg/SimpleHandle.msg
  msg/SimpleOccupancyGridArray.msg
  msg/SimpleOccupancyGrid.msg
  msg/SlicedPointCloud.msg
  msg/SnapItRequest.msg
  msg/SparseImage.msg
  msg/SparseOccupancyGridArray.msg
  msg/SparseOccupancyGridCell.msg
  msg/SparseOccupancyGridColumn.msg
  msg/SparseOccupancyGrid.msg
  msg/Spectrum.msg
  msg/TimeRange.msg
  msg/TorusArray.msg
  msg/Torus.msg
  msg/TrackerStatus.msg
  msg/TrackingStatus.msg
  msg/BoolStamped.msg
  msg/VectorArray.msg
  msg/VQAResult.msg
  msg/WeightedPoseArray.msg
  msg/ContactSensor.msg
  msg/ContactSensorArray.msg
  msg/PlotDataArray.msg
  msg/Segment.msg
  msg/SegmentStamped.msg
  msg/SegmentArray.msg
  msg/PeoplePose.msg
  msg/PeoplePoseArray.msg
  msg/HandPose.msg
  msg/HandPoseArray.msg  
  DEPENDENCIES std_msgs sensor_msgs geometry_msgs pcl_msgs builtin_interfaces  
)



set(action_files
  
  
  DEPENDENCIES std_msgs builtin_interfaces
)

# Generate messages, services and actions
rosidl_generate_interfaces(${PROJECT_NAME}
  "srv/CallPolygon.srv"
  "srv/CallSnapIt.srv"
  "srv/CheckCircle.srv"
  "srv/CheckCollision.srv"
  "srv/EnvironmentLock.srv"
  "srv/EuclideanSegment.srv"
  "srv/ICPAlign.srv"
  "srv/ICPAlignWithBox.srv"
  "srv/NonMaximumSuppression.srv"
  "srv/PolygonOnEnvironment.srv"
  "srv/RobotPickupReleasePoint.srv"
  "srv/SaveMesh.srv"
  "srv/SetDepthCalibrationParameter.srv"
  "srv/SetLabels.srv"
  "srv/SetPointCloud2.srv"
  "srv/SetTemplate.srv"
  #"srv/SnapFootstep.srv"
  "srv/SwitchTopic.srv"
  "srv/TowerPickUp.srv"
  "srv/TowerRobotMoveCommand.srv"
  "srv/TransformScreenpoint.srv"
  "srv/UpdateOffset.srv"
  "srv/WhiteBalancePoints.srv"
  "srv/WhiteBalance.srv"
  "action/VQATask.action"
  "action/ClassificationTask.action"
  ${msg_files}
  ${srv_files}
  ${action_files}
  DEPENDENCIES std_msgs sensor_msgs geometry_msgs pcl_msgs builtin_interfaces
)

# Declare package dependencies
#ament_export_dependencies(rosidl_default_runtime)

# Install directories
install(DIRECTORY sample scripts
  DESTINATION share/${PROJECT_NAME}
  USE_SOURCE_PERMISSIONS
)





if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  ament_lint_auto_find_test_dependencies()
  
  find_package(ament_cmake_gtest REQUIRED)
  # Add your tests here using ament_add_gtest
  # Example: ament_add_gtest(test_name test_source.cpp)
endif()

ament_package()
