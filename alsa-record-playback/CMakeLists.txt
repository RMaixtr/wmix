cmake_minimum_required(VERSION 3.10)
project(alsa_record)

# 设置C++标准
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# 查找ALSA库
find_package(ALSA REQUIRED)

# 添加可执行文件
add_executable(record
    record.cpp
    alsa_capture.cpp
)
 
add_executable(playback
    playback.cpp
    alsa_playback.cpp
)

# 链接ALSA库
target_link_libraries(record
    PRIVATE
    asound
)

 

target_link_libraries(playback
    PRIVATE
    asound
)

# 添加头文件搜索路径
target_include_directories(record
    PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}
)

target_include_directories(playback
    PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}
) 