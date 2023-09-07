cmake_minimum_required(VERSION 3.14)

add_library(ble STATIC
    ble.c
)

pico_btstack_make_gatt_header(ble PRIVATE "${CMAKE_CURRENT_LIST_DIR}/ble_gatt.gatt")

target_link_libraries(ble
    pico_btstack_ble
    pico_btstack_cyw43
    pico_cyw43_arch_none
    hardware_clocks
    )

target_include_directories(ble 
    PRIVATE 
        private
    PUBLIC
        .
)