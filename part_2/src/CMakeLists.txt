ADD_EXECUTABLE(main hello.cpp)

#ADD_LIBRARY(helloa SHARED ${SRC})

FIND_PACKAGE(PCL REQUIRED COMPONENTS common io)
if(PCL_FOUND)
	ADD_DEFINITIONS(${PCL_DEFINITIONS})
	INCLUDE_DIRECTORIES(${PCL_INCLUDE_DIRS})
	LINK_LIBRARIES(${PCL_LIBRARY_DIRS})
else(PCL_FOUND)
    message(FATAL_ERROR "PCL not found!")
endif(PCL_FOUND)

FIND_PACKAGE(OpenCV REQUIRED)
if(OpenCV_FOUND)
	INCLUDE_DIRECTORIES(${OPENCV_INCLUDE_DIRS})
	LINK_LIBRARIES(${OPENCV_LIBRARY_DIRS})
else(OpenCV_FOUND)
	message(FATAL_ERROR "opencv not found!")
endif(OpenCV_FOUND)


ADD_EXECUTABLE(generate_point_cloud generatePointCloud.cpp)
TARGET_LINK_LIBRARIES(generate_point_cloud ${OpenCV_LIBS} ${PCL_LIBRARIES})


	
