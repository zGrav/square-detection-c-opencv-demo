cmake_minimum_required(VERSION 2.8)
project( squares )

message(STATUS "start running cmake...")

find_package(Boost 1.66.0 COMPONENTS system filesystem REQUIRED)

if(Boost_FOUND)

    message(STATUS "Boost_INCLUDE_DIRS: ${Boost_INCLUDE_DIRS}")
    message(STATUS "Boost_LIBRARIES: ${Boost_LIBRARIES}")
    message(STATUS "Boost_VERSION: ${Boost_VERSION}")

    include_directories(${Boost_INCLUDE_DIRS})

endif()

find_package( OpenCV REQUIRED )
add_executable( squares squares.cpp )
target_link_libraries( squares ${OpenCV_LIBS} )

if(Boost_FOUND)

    target_link_libraries( squares ${Boost_LIBRARIES} )

endif()
