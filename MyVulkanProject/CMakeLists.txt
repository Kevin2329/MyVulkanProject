# CMakeList.txt : CMake project for MyVulkanProject, include source and define
# project specific logic here.
#
cmake_minimum_required (VERSION 3.8)

include_directories("E:/Vulkan/Include" "E:/glfw/include")

# Add source to this project's executable.
add_executable (MyVulkanProject "MyVulkanProject.cpp" "MyVulkanProject.h")


find_library(VULKAN_LIBRARY vulkan-1 PATHS "E:/Vulkan/Lib/vulkan-1.lib") # 查找 vulkan 库，指定路径为 "E:/Vulkan/Lib"
if (VULKAN_LIBRARY)
  target_link_libraries(MyVulkanProject PRIVATE ${VULKAN_LIBRARY}) # 将 vulkan 库链接到项目中
else()
  message(FATAL_ERROR "Could not find vulkan library")
endif()

find_library(GLFW_LIBRARY glfw3 PATHS "E:/glfw/build/src/Debug/glfw3dll.lib") 
if (GLFW_LIBRARY)
  target_link_libraries(MyVulkanProject PRIVATE ${GLFW_LIBRARY})
else()
  message(FATAL_ERROR "Could not find glfw library")
endif()


if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET MyVulkanProject PROPERTY CXX_STANDARD 20)
endif()

# TODO: Add tests and install targets if needed.
