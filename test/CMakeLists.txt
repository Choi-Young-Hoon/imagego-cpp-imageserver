set(SOURCES main.cpp
            test.cpp
)

set(IMAGE_SERVER_TEST imageserver_test)

enable_testing() # build/test Æú´õ »ý¼ºµÊ

add_executable(${IMAGE_SERVER_TEST} ${SOURCES})

find_package(GTest CONFIG REQUIRED)
target_link_libraries(${IMAGE_SERVER_TEST} PRIVATE ${PROJECT_NAME}
                                              GTest::gtest
                                              GTest::gtest_main
                                              GTest::gmock
                                              GTest::gmock_main)

target_include_directories(${IMAGE_SERVER_TEST} PRIVATE ${IMAGESERVER_INCLUDE_DIR})