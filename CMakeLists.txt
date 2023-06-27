cmake_minimum_required(VERSION 3.12)

# Pull in SDK (must be before project)
include(pico_sdk_import.cmake)

# include(pico_extras_import_optional.cmake)

project(pico-logger-firmware)

# project(pico-logger C CXX ASM)
# set(CMAKE_C_STANDARD 11)
# set(CMAKE_CXX_STANDARD 17)

# if (PICO_SDK_VERSION_STRING VERSION_LESS "1.3.0")
#     message(FATAL_ERROR "Raspberry Pi Pico SDK version 1.3.0 (or later) required. Your version is ${PICO_SDK_VERSION_STRING}")
# endif()

# set(PICO_EXAMPLES_PATH ${PROJECT_SOURCE_DIR})

# Initialize the SDK
pico_sdk_init()
add_subdirectory(src)

add_executable(pico-logger-firmware
        src/main.c
        src/msc_disk.c
        src/usb_descriptors.c
    )

# target_link_libraries(main pico_stdlib)

pico_add_extra_outputs(pico-logger-firmware)

set(FAMILY rp2040)
set(BOARD pico_sdk)

target_include_directories(pico-logger-firmware PUBLIC
        ${CMAKE_CURRENT_LIST_DIR}/src)

target_link_libraries(pico-logger-firmware PUBLIC 
pico_stdlib 
# pico_unique_id 
tinyusb_device 
tinyusb_board
)


# dd_executable(hello_world
#         hello_world.c
#     )

# include(example_auto_set_url.cmake)
# # Add blink example
# add_subdirectory(blink)

# # Add hello world example
# add_subdirectory(hello_world)

# add_compile_options(-Wall
#         -Wno-format          # int != int32_t as far as the compiler is concerned because gcc has int32_t as long int
#         -Wno-unused-function # we have some for the docs that aren't called
#         )
# if (CMAKE_C_COMPILER_ID STREQUAL "GNU")
#     add_compile_options(-Wno-maybe-uninitialized)
# endif()

# # Hardware-specific examples in subdirectories:

# add_subdirectory(clocks)
# add_subdirectory(cmake)
# add_subdirectory(divider)
# add_subdirectory(dma)
# add_subdirectory(flash)
# add_subdirectory(gpio)
# add_subdirectory(i2c)
# add_subdirectory(interp)
# add_subdirectory(multicore)
# add_subdirectory(picoboard)
# add_subdirectory(pico_w)
# add_subdirectory(pio)
# add_subdirectory(pwm)
# add_subdirectory(reset)
# add_subdirectory(rtc)
# add_subdirectory(spi)
# add_subdirectory(system)
# add_subdirectory(timer)
# add_subdirectory(uart)
# add_subdirectory(usb)
# add_subdirectory(watchdog)
