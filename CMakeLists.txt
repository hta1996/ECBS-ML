project(ECBS)

cmake_minimum_required (VERSION 2.8.12)

set(CMAKE_CXX_STANDARD 11)
SET(CMAKE_CXX_COMPILER "/spack/apps/gcc/4.9.4/bin/gcc")
SET(CMAKE_C_COMPILER "/spack/apps/gcc/4.9.4/bin/gcc")

set(CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS} -g -Wall --std=c++11")
set(CMAKE_CXX_FLAGS_DEBUG "-O0")
set(CMAKE_CXX_FLAGS_RELEASE "-O3 -DNDEBUG")

include_directories("inc" "src" "/scratch/taoanhua/sparsehash/include")

file(GLOB SOURCES "*src/*.cpp" "*.cpp")
 
add_definitions(-D_GLIBCXX_USE_CXX11_ABI=0)

# Find Boost
find_package( Boost 1.49.0 REQUIRED COMPONENTS program_options system filesystem)
include_directories( ${Boost_INCLUDE_DIRS} )

add_executable(ECBS ${SOURCES})
target_link_libraries(ECBS ${Boost_LIBRARIES} -lstdc++ -lm)
