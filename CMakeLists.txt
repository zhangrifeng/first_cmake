cmake_minimum_required(VERSION 3.10.0)
project(planning)
set(CMAKE_CXX_STANDARD 17)


# 可执行文件.exe和动态库.dll的输出路径
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin)


# 抓取src目录下的所有.cpp文件，将文件名存入DIR_SRCS变量中
# 为上面的所有.cpp文件生成动态库，名字为common,就是最后在.exe同级下会生成一个libcommon.dll文件
aux_source_directory(${PROJECT_SOURCE_DIR}/src DIR_SRCS)
add_library(common
SHARED
${DIR_SRCS}
)


# 动态库common的头文件路径，这样planning_main.cpp就可以include这个头文件了
target_include_directories(common
PUBLIC
${PROJECT_SOURCE_DIR}/include
)


# 生成的可执行文件也要包含头文件路径
add_executable(planning_main planning_main.cpp)

target_include_directories(planning_main
PUBLIC
${PROJECT_SOURCE_DIR}/include
)
# 可执行文件链接动态库
target_link_libraries(planning_main
PUBLIC
common
)

