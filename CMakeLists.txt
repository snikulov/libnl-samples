cmake_minimum_required(VERSION 3.23)

project(libnl-examples)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

find_package(libnl REQUIRED)

aux_source_directory(src LIBNL_EXAMPLES_SRC)

# compile each file
foreach (_main_file ${LIBNL_EXAMPLES_SRC})
  get_filename_component(_main_name ${_main_file} NAME_WE)
  add_executable(${_main_name} ${_main_file})
  target_link_libraries(${_main_name} PRIVATE libnl::libnl)
  target_include_directories(${_main_name} PRIVATE include)
endforeach ()
