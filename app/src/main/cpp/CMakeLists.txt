cmake_minimum_required(VERSION 3.22.1)

project("RPO")

add_library(rpo SHARED native-lib.cpp)

add_library(spdlog STATIC IMPORTED)

set_target_properties(spdlog PROPERTIES IMPORTED_LOCATION
        C:/Users/Solnyyysko/AndroidStudioProjects/libs/spdlog/build/${ANDROID_ABI}/libspdlog.a)

target_include_directories(rpo PUBLIC
        C:/Users/Solnyyysko/AndroidStudioProjects/libs/spdlog/spdlog/include)

find_library(log-lib log)

target_link_libraries(
        rpo
        spdlog
        ${log-lib})