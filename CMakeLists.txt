cmake_minimum_required(VERSION 3.10.2)

project(qthttpserver LANGUAGES CXX)

set(CMAKE_INCLUDE_CURRENT_DIR ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Qt5 COMPONENTS
        Core
	Network
        REQUIRED)
file(GLOB SOURCES
    ${PROJECT_SOURCE_DIR}/src/3rdparty/http-parser/*.h
    ${PROJECT_SOURCE_DIR}/src/3rdparty/http-parser/*.c
    ${PROJECT_SOURCE_DIR}/src/3rdparty/http-parser/contrib/*.c

    ${PROJECT_SOURCE_DIR}/src/httpserver/*.h
    ${PROJECT_SOURCE_DIR}/src/httpserver/*.cpp
    )
add_library(${PROJECT_NAME} STATIC ${SOURCES})
target_include_directories(${PROJECT_NAME} PUBLIC ${PROJECT_SOURCE_DIR}/src/httpserver)
target_link_libraries(${PROJECT_NAME}
    Qt5::Core
    Qt5::Network
    )

