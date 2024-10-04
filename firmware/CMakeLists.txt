cmake_minimum_required(VERSION 3.13...3.27)

set(PICO_SDK_PATH "${CMAKE_CURRENT_SOURCE_DIR}/external/pico-sdk")


option(AUTO_DOWNLOAD_SDK "Automatically download the pico_sdk" OFF)

if(EXISTS "${PICO_SDK_PATH}/pico_sdk_init.cmake")
    message(STATUS "Submodule init. Using it")
    include("${PICO_SDK_PATH}/pico_sdk_init.cmake")
else()
    if(AUTO_DOWNLOAD_SDK)
        set(PICO_SDK_FETCH_FROM_GIT on)
    endif()
    include("cmake/pico_sdk_import.cmake")
endif()


project(PicoCartridge)

# initialize the Raspberry Pi Pico SDK
pico_sdk_init()

# rest of your project