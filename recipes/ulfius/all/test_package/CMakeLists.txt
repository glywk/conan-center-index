cmake_minimum_required(VERSION 3.15)
project(test_package LANGUAGES C)

find_package(Ulfius REQUIRED CONFIG)

option(ULFIUS_SHARED "Ulfius is built as a shared library")

add_executable(${PROJECT_NAME} test_package.c)
if(ULFIUS_SHARED)
    target_link_libraries(${PROJECT_NAME} PRIVATE Ulfius::Ulfius)
else()
    target_link_libraries(${PROJECT_NAME} PRIVATE Ulfius::Ulfius-static)
endif()
