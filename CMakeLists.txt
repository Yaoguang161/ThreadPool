cmake_minimum_required(VERSION 3.16.3)
project(ThreadPool LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 11)    ## 设置语言版本
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)  ##取消额外语法
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)  ##clang的相关内容


SET(CMAKE_BUILD_TYPE "Debug") 
# 添加对gdb的支持
SET(CMAKE_CXX_FLAGS_DEBUG "$ENV{CXXFLAGS} -O0 -Wall -g2 -ggdb")
SET(CMAKE_CXX_FLAGS_RELEASE "$ENV{CXXFLAGS} -O3 -Wall")



find_package(Threads) ##引入外部依赖包

add_executable(main)   ##这里的ThreadPool
target_link_libraries (main ${CMAKE_THREAD_LIBS_INIT}) ##链接 Thread 库
file(GLOB_RECURSE sources CONFIGURE_DEPENDS src/*.cpp src/*.h)
target_sources(main PUBLIC ${sources})    ##和这里的ThreadPool全局唯一,是运行文件的名字 build/ThreadPool运行