cmake_minimum_required(VERSION 3.22.1)

project("RPO")

add_library(RPO SHARED native-lib.cpp)

add_library(spdlog STATIC IMPORTED)
add_library(mbedcrypto SHARED IMPORTED)

set_target_properties(spdlog PROPERTIES IMPORTED_LOCATION
        C:/Users/Solnyyysko/AndroidStudioProjects/libs/spdlog/build/${ANDROID_ABI}/libspdlog.a)
set_target_properties(mbedcrypto PROPERTIES IMPORTED_LOCATION
        ${CMAKE_CURRENT_SOURCE_DIR}/../nativeLibs/${ANDROID_ABI}/libmbedcrypto.so)

target_include_directories(RPO PUBLIC
        C:/Users/Solnyyysko/AndroidStudioProjects/libs/spdlog/spdlog/include)
target_include_directories(RPO PUBLIC
        C:/Users/Solnyyysko/AndroidStudioProjects/libs/mbedtls/mbedtls/include)

find_library(log-lib log)

target_link_libraries(
        RPO
        spdlog
        mbedcrypto
        ${log-lib})
