cmake_minimum_required(VERSION 4.4.0)

#> https://github.com/Kitware/CMake/blob/master/Help/dev/experimental.rst - Whenever this needs to swap, just choose the right tag
set(CMAKE_EXPERIMENTAL_CXX_IMPORT_STD "f35a9ac6-8463-4d38-8eec-5d6008153e7d")
set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_MODULE_STD ON)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

project(userspawn LANGUAGES CXX)

find_package(PkgConfig REQUIRED)
pkg_check_modules(DBUS REQUIRED IMPORTED_TARGET dbus-1)

add_executable(userspawn main.cpp)

target_link_libraries(userspawn PRIVATE PkgConfig::DBUS)

install(TARGETS userspawn
    RUNTIME DESTINATION bin
)
