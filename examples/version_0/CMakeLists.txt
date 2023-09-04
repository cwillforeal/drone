cmake_minimum_required(VERSION 3.14)

set(EXE_NAME version_0)

# Make project data accessible to compiler
add_compile_definitions(BUILD_NUM=${BUILD_NUMBER})

# Include app source code file(s)
add_executable(${EXE_NAME}
    main.c
)

# Link to built libraries
target_link_libraries(${EXE_NAME} LINK_PUBLIC
    pico_stdlib
    FreeRTOS)

# Enable/disable STDIO via USB and UART
pico_enable_stdio_usb(${EXE_NAME} 1)
pico_enable_stdio_uart(${EXE_NAME} 0)

# Enable extra build products
pico_add_extra_outputs(${EXE_NAME})
