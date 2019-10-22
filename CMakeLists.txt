cmake_minimum_required(VERSION 3.13)

project(filesentry)

add_library(filesentry source/FileWatcher.cpp source/FileWatcherLinux.cpp source/FileWatcherWin32.cpp source/FileWatcherOSX.cpp)

target_include_directories(filesentry PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include)
