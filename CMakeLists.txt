
cmake_minimum_required(VERSION 3.16)
project(entt_snapshot)

set(CXX_STANDARD 20)
set(CXX_STANDARD_REQUIRED True)
set(CMAKE_BUILD_TYPE Debug)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

find_package(EnTT CONFIG REQUIRED)
find_package(cereal REQUIRED)

file(GLOB_RECURSE sources "src/**.cpp")

add_library(entt_snapshot SHARED
    ${sources}
)
target_link_libraries(entt_snapshot EnTT::EnTT cereal::cereal)

target_include_directories(entt_snapshot
    PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include
    PUBLIC ${EnTT_INCLUDE_DIRS}  # Add this line to include EnTT directories
    PUBLIC ${cereal_INCLUDE_DIRS}  # Add this line to include cereal directories
)