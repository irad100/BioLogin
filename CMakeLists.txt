cmake_minimum_required(VERSION 3.14)
project(BioLogin)


include(FetchContent)

FetchContent_Declare(
   dlib
   GIT_REPOSITORY https://github.com/davisking/dlib.git
   GIT_TAG        master
)
FetchContent_MakeAvailable(dlib)

find_package( OpenCV REQUIRED )
include_directories( ${OpenCV_INCLUDE_DIRS} )

add_executable(dnn_face_recognition_ex dnn_face_recognition_ex.cpp)
target_link_libraries(dnn_face_recognition_ex dlib::dlib)

add_executable(webcam_face_pose_ex webcam_face_pose_ex.cpp)
target_link_libraries(webcam_face_pose_ex dlib::dlib ${OpenCV_LIBS} )