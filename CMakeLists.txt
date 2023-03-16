cmake_minimum_required(VERSION 3.21)

project(magewell LANGUAGES C CXX VERSION 0.0.0)

if (${CMAKE_SYSTEM_PROCESSOR} STREQUAL "x86_64")
    set(_folder "x64")
elseif(${CMAKE_SYSTEM_PROCESSOR} STREQUAL "i386")
    set(_folder "i386")
elseif(${CMAKE_SYSTEM_PROCESSOR} STREQUAL "i686")
    set(_folder "i386")
elseif(${CMAKE_SYSTEM_PROCESSOR} STREQUAL "aarch64")
    set(_folder "arm64")
elseif(${CMAKE_SYSTEM_PROCESSOR} STREQUAL "aarch32")
    set(_folder "arm32")
else()
    message(FATAL_ERROR "Unsupported architecture : ${CMAKE_SYSTEM_PROCESSOR}")
endif()

file(GLOB _libFiles
     "${CMAKE_SOURCE_DIR}/src/Lib/${_folder}/*.a"
)

install(FILES ${_libFiles}
        DESTINATION ${CMAKE_INSTALL_LIBDIR})

install(DIRECTORY ${CMAKE_SOURCE_DIR}/src/Include/
        DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/${PROJECT_NAME})
