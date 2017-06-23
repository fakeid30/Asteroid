cmake_minimum_required(VERSION 3.7)


project(Asteroids)

set(EXECUTABLE_NAME "Asteroids")
add_executable(${EXECUTABLE_NAME} main.cpp)


# Detect and add SFML
set(CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}/cmake_modules" ${CMAKE_MODULE_PATH})
#Find any version 2.X of SFML
#See the FindSFML.cmake file for additional details and instructions
find_package(SFML 2 REQUIRED network audio graphics window system)
if (SFML_FOUND)
    include_directories(${SFML_INCLUDE_DIR})
    target_link_libraries(${EXECUTABLE_NAME} ${SFML_LIBRARIES} ${SFML_DEPENDENCIES})
endif ()


# Install target
install(TARGETS ${EXECUTABLE_NAME} DESTINATION bin)


# CPack packaging
include(InstallRequiredSystemLibraries)
set(CPACK_RESOURCE_FILE_LICENSE "${CMAKE_SOURCE_DIR}/COPYING")
set(CPACK_PACKAGE_VERSION_MAJOR "${Asteroids_VERSION_MAJOR}")
set(CPACK_PACKAGE_VERSION_MINOR "${Asteroids_VERSION_MINOR}")
include(CPack)
# t1.loadFromFile("/home/nirjhor/Asteroid/images/spaceship.png");
#    t2.loadFromFile("/home/nirjhor/Asteroid/images/background.jpg");
