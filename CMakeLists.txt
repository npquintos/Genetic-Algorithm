include(CMakePrintHelpers)
project(ex1 LANGUAGES CXX)
cmake_minimum_required(VERSION 3.6 FATAL_ERROR)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_CXX_STANDARD_REQUIRED ON) 

set(GA_INCLUDE_DIR "/path/to/genetic/galib247")
set(GA "${GA_INCLUDE_DIR}/ga")

file(GLOB ga_sources ${GA}/*.C)
# cmake_print_variables(ga_sources)

LIST(APPEND flags
    "-g"
    "-DLINUX"
    "-DUNIX"
    "-Wall"
    "-Wextra"
    "-pedantic"
    # "-D_REENTRANT"
    "-fPIC"
    # "-DOSI64"
    )

add_executable(ex1 ex1.C ${ga_sources})

target_include_directories(ex1
    PUBLIC
        ${GA_INCLUDE_DIR}
    )

target_compile_options(ex1
    PRIVATE
        ${flags}
    )
