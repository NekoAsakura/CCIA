cmake_minimum_required(VERSION 3.15)
project(CCIA)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}/bin")

file(GLOB_RECURSE SOURCES CONFIGURE_DEPENDS "${CMAKE_SOURCE_DIR}/listings/listing_*.cpp")

foreach(SRC IN LISTS SOURCES)
    get_filename_component(BASENAME "${SRC}" NAME)
    string(REGEX REPLACE "\\.cpp$" "" TARGET_NAME "${BASENAME}")
    add_executable("${TARGET_NAME}" "${SRC}")
    set_target_properties("${TARGET_NAME}" PROPERTIES 
        RUNTIME_OUTPUT_DIRECTORY "${CMAKE_RUNTIME_OUTPUT_DIRECTORY}/${TARGET_NAME}")
endforeach()
