# Generated Cmake Pico project file

cmake_minimum_required(VERSION 3.13)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

# initalize pico_sdk from installed location
# (note this can come from environment, CMake cache etc)
set(PICO_SDK_PATH "/home/pi/pico/pico-sdk")

# Pull in Raspberry Pi Pico SDK (must be before project)
include(pico_sdk_import.cmake)

project(IndependentHID C CXX ASM)

set(PICO_CXX_ENABLE_EXCEPTIONS 1)

# Initialise the Raspberry Pi Pico SDK
pico_sdk_init()

# Add executable. Default name is the project name, version 0.1

add_executable(IndependentHID IndependentHID.cpp usb_descriptors.c )

target_include_directories(IndependentHID PRIVATE include/)

pico_set_program_name(IndependentHID "IndependentHID")
pico_set_program_version(IndependentHID "0.1")

pico_enable_stdio_uart(IndependentHID 1)
pico_enable_stdio_usb(IndependentHID 0)

# Add the standard library to the build
target_link_libraries(IndependentHID
    pico_stdlib
    tinyusb_device
    tinyusb_board
)

pico_add_extra_outputs(IndependentHID)

