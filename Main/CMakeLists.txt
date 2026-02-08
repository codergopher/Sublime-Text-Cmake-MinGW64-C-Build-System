cmake_minimum_required (VERSION 4.1)

project (Main)

#Compiler flags
set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++17 -m64 -g -Wall -fno-omit-frame-pointer -L ")

set (source_dir "${PROJECT_SOURCE_DIR}/src")

#We want to output our .exe to the "bin" dir, and if we make any .a or .dll.a files we'll output them to "lib"
set (CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/bin")
set (CMAKE_LIBRARY_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/lib")
set (CMAKE_ARCHIVE_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/lib")

#This list should contain all your include directories
set (include_list "")
#list (APPEND include_list "C:/Users/getma/Downloads/SDL3-devel-3.4.0-mingw/SDL3-3.4.0/x86_64-w64-mingw32/include") 


#This list should contain all your link libraries, such as .a files for static linking, and .dll.a files for dynamic linking
#If you have a library installed via MSYS2 you can append it to the list with just -lfoo for example
set (lib_list "")
list (APPEND lib_list "-lSDL3")

file (GLOB_RECURSE source_files "${source_dir}/*.cpp")

add_executable (Main ${source_files})

target_link_libraries(Main PRIVATE ${lib_list})

target_include_directories(Main PRIVATE src ${include_list})