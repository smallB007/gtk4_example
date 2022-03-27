cmake_minimum_required(VERSION 3.0.0)
project(gtk4_example_app VERSION 0.1.0)

set(CMAKE_CXX_STANDARD 20)

find_package(PkgConfig REQUIRED)
pkg_check_modules(GTK4 REQUIRED gtk4)

include_directories(${GTK4_INCLUDE_DIRS})
link_directories(${GTK4_LIBRARY_DIRS})

add_definitions(${GTK4_CFLAGS_OTHER})

include(CTest)
enable_testing()

add_executable(gtk4_example_app main.cpp)

target_link_libraries(gtk4_example_app ${GTK4_LIBRARIES})

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)

install(TARGETS gtk4_example_app RUNTIME DESTINATION bin) 


