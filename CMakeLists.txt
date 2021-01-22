cmake_minimum_required(VERSION 3.12)

# Pull in PICO SDK (must be before project)
include(pico_sdk_import.cmake)

project(pico_examples C CXX ASM)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

# Initialize the SDK
pico_sdk_init()

add_executable(pico-project
  main.c
)

# Make the stdio functions use USB rather than the serial pins
pico_enable_stdio_usb(pico-project 1)
pico_enable_stdio_uart(pico-project 0)

# Pull in our pico_stdlib which pulls in commonly used features
target_link_libraries(pico-project pico_stdlib)

# create map/bin/hex file etc.
pico_add_extra_outputs(pico-project)
