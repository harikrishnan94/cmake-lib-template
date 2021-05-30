find_package(doctest CONFIG REQUIRED)

add_executable(MyLibTest testbase.cpp testmylib.cpp)
target_compile_features(
    MyLib
    INTERFACE cxx_std_17
    PRIVATE cxx_std_17)
target_link_libraries(MyLibTest PRIVATE MyLib doctest::doctest)
add_warning_flags(MyLibTest)
add_sanitizer_flags(MyLibTest)

add_test(NAME MyLibTest COMMAND MyLibTest -d yes)
