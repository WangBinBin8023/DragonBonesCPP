# 指定 tremolo 库的源代码路径  
cmake_minimum_required(VERSION 3.6)  
project(tremolo_lib)

# 添加头文件搜索路径
include_directories(./)
include_directories(./3rdParty/)
include_directories(./DragonBones/src/)
include_directories(./DragonBones/src/dragonBones/core/)
include_directories(./DragonBones/src/dragonBones/parsers/)

# 获取当前目录下的所有 .h 文件
file(GLOB HEADER_FILES "*.cpp")

# 添加要编译的源文件  
add_library(DragonBones
./DragonBones/src/dragonBones/model/TimelineData.cpp
./DragonBones/src/dragonBones/model/DragonBonesData.cpp
./DragonBones/src/dragonBones/model/ArmatureData.cpp
./DragonBones/src/dragonBones/model/FrameData.cpp
./DragonBones/src/dragonBones/model/AnimationData.cpp
./DragonBones/src/dragonBones/textures/TextureData.cpp
./DragonBones/src/dragonBones/animation/WorldClock.cpp
./DragonBones/src/dragonBones/animation/Animation.cpp
./DragonBones/src/dragonBones/animation/AnimationState.cpp
./DragonBones/src/dragonBones/animation/TimelineState.cpp
./DragonBones/src/dragonBones/events/EventObject.cpp
./DragonBones/src/dragonBones/core/BaseObject.cpp
./DragonBones/src/dragonBones/armature/Slot.cpp
./DragonBones/src/dragonBones/armature/Armature.cpp
./DragonBones/src/dragonBones/armature/Bone.cpp
./DragonBones/src/dragonBones/factories/BaseFactory.cpp
./DragonBones/src/dragonBones/parsers/JSONDataParser.cpp
./DragonBones/src/dragonBones/parsers/DataParser.cpp
)

include_directories(./DragonBones/src/dragonBones/model/) 
add_executable(DragonBones_test DragonBones_test.cpp)
target_link_libraries(DragonBones_test PRIVATE DragonBones) 

# 获取当前目录下的所有 .h 文件
file(GLOB_RECURSE HEADER_FILES_model "./DragonBones/src/dragonBones/model/*.h")
file(GLOB_RECURSE HEADER_FILES_textures "./DragonBones/src/dragonBones/textures/*.h")
file(GLOB_RECURSE HEADER_FILES_animation "./DragonBones/src/dragonBones/animation/*.h")
file(GLOB_RECURSE HEADER_FILES_events "./DragonBones/src/dragonBones/events/*.h")
file(GLOB_RECURSE HEADER_FILES_geom "./DragonBones/src/dragonBones/geom/*.h")
file(GLOB_RECURSE HEADER_FILES_core "./DragonBones/src/dragonBones/core/*.h")
file(GLOB_RECURSE HEADER_FILES_armature "./DragonBones/src/dragonBones/armature/*.h")
file(GLOB_RECURSE HEADER_FILES_factories "./DragonBones/src/dragonBones/factories/*.h")
file(GLOB_RECURSE HEADER_FILES_parsers "./DragonBones/src/dragonBones/parsers/*.h")

# 安装库文件
install(TARGETS DragonBones DESTINATION ${CMAKE_INSTALL_PREFIX}/lib)
install(FILES ${HEADER_FILES_model} DESTINATION ${CMAKE_INSTALL_PREFIX}/include/model/)
install(FILES ${HEADER_FILES_textures} DESTINATION ${CMAKE_INSTALL_PREFIX}/include/textures/)
install(FILES ${HEADER_FILES_animation} DESTINATION ${CMAKE_INSTALL_PREFIX}/include/animation/)
install(FILES ${HEADER_FILES_events} DESTINATION ${CMAKE_INSTALL_PREFIX}/include/events/)
install(FILES ${HEADER_FILES_geom} DESTINATION ${CMAKE_INSTALL_PREFIX}/include/geom/)
install(FILES ${HEADER_FILES_core} DESTINATION ${CMAKE_INSTALL_PREFIX}/include/core/)
install(FILES ${HEADER_FILES_armature} DESTINATION ${CMAKE_INSTALL_PREFIX}/include/armature/)
install(FILES ${HEADER_FILES_factories} DESTINATION ${CMAKE_INSTALL_PREFIX}/include/factories/)
install(FILES ${HEADER_FILES_parsers} DESTINATION ${CMAKE_INSTALL_PREFIX}/include/parsers/)

