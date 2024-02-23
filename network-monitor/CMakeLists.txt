cmake_minimum_required(VERSION 3.27)

project(network-monitor)

find_package(Boost 1.74 REQUIRED COMPONENTS system)

# Static library
set(LIB_SOURCES
    "${CMAKE_CURRENT_SOURCE_DIR}/src/websocket-client.cpp"
)
add_library(network-monitor STATIC ${LIB_SOURCES})
target_compile_features(network-monitor
    PUBLIC
        cxx_std_14
)
target_include_directories(network-monitor
    PUBLIC
        inc
)
target_link_libraries(network-monitor
    PUBLIC
        boost::boost
)

# Source
set(SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/src/main.cpp")
add_executable(network-monitor-binary ${SOURCES})
target_compile_features(network-monitor-binary
    PRIVATE
        cxx_std_17
)

target_link_libraries(network-monitor-binary
    PRIVATE
        network-monitor
)
