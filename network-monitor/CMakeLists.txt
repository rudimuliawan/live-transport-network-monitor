cmake_minimum_required(VERSION 3.27)

project(network-monitor)

find_package(Boost 1.74 REQUIRED COMPONENTS system)

set(SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/src/main.cpp")

add_executable(network-monitor ${SOURCES})
target_compile_features(network-monitor
    PRIVATE
        cxx_std_17
)
target_link_libraries(network-monitor
    PRIVATE
        boost::boost
)
