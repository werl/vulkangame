cmake_minimum_required(VERSION 3.17)
include(ExternalProject)
project(vulkangame)

set(CMAKE_CXX_STANDARD 20)

find_package(Vulkan REQUIRED)

#GLM stuff
add_subdirectory(cust_include/glm)

#GLFW stuff
set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)

add_subdirectory(cust_include/glfw)

#spdlog stuff
add_subdirectory(cust_include/spdlog)

add_executable(vulkangame src/main.cpp)
target_compile_definitions(vulkangame PUBLIC cxx-exceptions)

target_link_libraries(vulkangame PUBLIC Vulkan::Vulkan glfw glm::glm spdlog::spdlog)