find_package(Threads REQUIRED)

add_library(MyLib libimpl.cpp)
target_include_directories(
    MyLib
    INTERFACE ${PROJECT_SOURCE_DIR}/include
    PRIVATE ${PROJECT_SOURCE_DIR}/include)
target_compile_features(
    MyLib
    INTERFACE cxx_std_17
    PRIVATE cxx_std_17)
target_link_libraries(MyLib PRIVATE Threads::Threads)
add_warning_flags(MyLib)
add_sanitizer_flags(MyLib)
