cmake_minimum_required(VERSION 3.4)
project(solver_application)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_executable(solver equation.cpp)

target_include_directories(solver PUBLIC
    ${CMAKE_CURRENT_SOURCE_DIR}/../formatter_ex_lib
    ${CMAKE_CURRENT_SOURCE_DIR}/../formatter_lib
    ${CMAKE_CURRENT_SOURCE_DIR}/../solver_lib
)

target_link_libraries(solver solver_lib formatter_ex formatter)
