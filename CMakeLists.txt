# CMakeList.txt : CMake project for LearningOpenGL, include source and define
# project specific logic here.
#
cmake_minimum_required (VERSION 3.8)

# Enable Hot Reload for MSVC compilers if supported.
if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

project ("setup")

#Add include directories
include_directories(AFTER include)


file(GLOB SETUP_SOURCE_FILE ${CMAKE_CURRENT_SOURCE_DIR}/src/setup.cpp)
file(GLOB SETUP_INCLUDE_FILE ${CMAKE_CURRENT_SOURCE_DIR}/include/setup.hpp)

# Add source to this project's executable.
add_executable (setup ${SETUP_SOURCE_FILE} ${SETUP_INCLUDE_FILE})

if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET setup PROPERTY CXX_STANDARD 20)
endif()

# TODO: Add tests and install targets if needed.
