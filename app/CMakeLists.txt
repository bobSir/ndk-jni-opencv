cmake_minimum_required(VERSION 3.4.1)

include_directories(src/main/cpp/include)
#编译源文件
file(GLOB my_source_path src/main/cpp/*.cpp src/main/cpp/*.c)
add_library(native-lib SHARED ${my_source_path})


add_library(lib_opencv SHARED IMPORTED)
set_target_properties(lib_opencv PROPERTIES IMPORTED_LOCATION ${CMAKE_SOURCE_DIR}/src/main/jniLibs/${ANDROID_ABI}/libopencv_java3.so)


target_link_libraries( # Specifies the target library.
        native-lib
        log
        jnigraphics
        lib_opencv)