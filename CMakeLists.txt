cmake_minimum_required(VERSION 3.0)
project(qTchat)
add_definitions("-fPIC")

# setting C++ version to 11
set(CMAKE_CXX_STANDARD 11)

if (MSVC)
    message ("-- Building for WINDOWS")
else (MSVC)
    message ("-- Building for LINUX")
endif (MSVC)


# logging CMAKE_MODULE_PATH
message("-- CMAKE_MODULE_PATH: \"" ${CMAKE_MODULE_PATH} "\"")

find_package(Qt5Widgets CONFIG REQUIRED)
find_package(Qt5Network CONFIG REQUIRED)

include_directories(${CMAKE_INCLUDE_PATH})


file(GLOB SRC Network/*.cpp *.cpp)
file(GLOB HEADERS Network/*.hpp *.hpp)

set(NETWORK_SOURCE_FILES
        Network/connection.cpp
        Network/main.cpp
        )

set(QT_PACKAGES
        Qt5::Widgets
        Qt5::Network
        Qt5::Gui
        )

set(CMAKE_AUTOMOC ON)

add_executable(qTchat ${NETWORK_SOURCE_FILES})
target_link_libraries(qTchat  ${QT_PACKAGES})
# logging all paths
