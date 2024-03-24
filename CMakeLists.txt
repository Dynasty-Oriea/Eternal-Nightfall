# CMakeList.txt : CMake project for Eternal Nightfall, include source and define
# project specific logic here.
#
cmake_minimum_required (VERSION 3.8)

# Enable Hot Reload for MSVC compilers if supported.
if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

project ("Eternal Nightfall")

# Add source to this project's executable.
add_executable (CMakeTarget "src/Eternal Nightfall.cpp" "include/Eternal Nightfall.h")

# Set SFML directory path
set(SFML_DIR "lib/SFML-2.6.1/lib/cmake/SFML")

# Find SFML
find_package(SFML 2.6 COMPONENTS system graphics audio network REQUIRED)

# Link SFML libraries
target_link_libraries(CMakeTarget PRIVATE sfml-audio sfml-graphics sfml-network sfml-system)

if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET CMakeTarget PROPERTY CXX_STANDARD 20)
endif()

# TODO: Add tests and install targets if needed.