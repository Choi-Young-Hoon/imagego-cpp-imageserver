cmake_minimum_required (VERSION 3.6)

project (imageserver)

set (CMAKE_CXX_STANDARD 20)
set (CMAKE_CXX_STANDARD_REQUIRED ON)

#set (CMAKE_CXX_FLAGS -Wall)
if (WIN32)

elseif (LINUX)
    set (CMAKE_CXX_FLAGS -Wall)
	set (CMAKE_CXX_FLAGS_RELEASE "-O3")
	set (CMAKE_CXX_FLAGS_DEBUG "-g")
endif ()

set (IMAGESERVER_INSTALL_DIR ${CMAKE_CURRENT_SOURCE_DIR}/build/imageserver)
set (IMAGESERVER_INCLUDE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/include)

add_library (${PROJECT_NAME})

find_package(Boost REQUIRED COMPONENTS system)
target_include_directories(${PROJECT_NAME} PUBLIC ${IMAGESERVER_INCLUDE_DIR}
                                                    ${Boost_INCLUDE_DIRS})
target_link_libraries(${PROJECT_NAME} PUBLIC Boost::system)

add_subdirectory(src)
add_subdirectory(test)