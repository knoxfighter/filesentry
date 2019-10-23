cmake_minimum_required(VERSION 3.13)

project(filesentry)

set(INSTALL_BIN_DIR "${CMAKE_INSTALL_PREFIX}/bin" CACHE PATH "Installation directory for executables")
set(INSTALL_LIB_DIR "${CMAKE_INSTALL_PREFIX}/lib" CACHE PATH "Installation directory for libraries")
set(INSTALL_INC_DIR "${CMAKE_INSTALL_PREFIX}/include" CACHE PATH "Installation directory for headers")

file(GLOB PSRC "${CMAKE_CURRENT_SOURCE_DIR}/include/filesentry/*.h")

add_library(filesentry STATIC source/FileWatcher.cpp source/FileWatcherLinux.cpp source/FileWatcherWin32.cpp source/FileWatcherOSX.cpp)

target_include_directories(filesentry PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include)

install(TARGETS filesentry
        RUNTIME DESTINATION "${INSTALL_BIN_DIR}"
        ARCHIVE DESTINATION "${INSTALL_LIB_DIR}"
        LIBRARY DESTINATION "${INSTALL_LIB_DIR}" )

install(FILES ${PSRC} DESTINATION "${INSTALL_INC_DIR}")
