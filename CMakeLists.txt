cmake_minimum_required(VERSION 3.0.0)
project(rgbd VERSION 0.1.0)

include(CTest)
enable_testing()

find_package(OpenCV)

add_executable(rgbd HLTRGB_PTP.cpp)

set(Arena_LIBS
    ${PROJECT_SOURCE_DIR}/lib64/libarena.so
    ${PROJECT_SOURCE_DIR}/lib64/libgentl.so
    ${PROJECT_SOURCE_DIR}/lib64/liblucidlog.so
    ${PROJECT_SOURCE_DIR}/lib64/libsave.so

    ${PROJECT_SOURCE_DIR}/GenICam/library/lib/Linux64_x64/libGCBase_gcc54_v3_3_LUCID.so
    ${PROJECT_SOURCE_DIR}/GenICam/library/lib/Linux64_x64/libGenApi_gcc54_v3_3_LUCID.so
    ${PROJECT_SOURCE_DIR}/GenICam/library/lib/Linux64_x64/libLog_gcc54_v3_3_LUCID.so
    ${PROJECT_SOURCE_DIR}/GenICam/library/lib/Linux64_x64/liblog4cpp_gcc54_v3_3_LUCID.so
    ${PROJECT_SOURCE_DIR}/GenICam/library/lib/Linux64_x64/libMathParser_gcc54_v3_3_LUCID.so
    ${PROJECT_SOURCE_DIR}/GenICam/library/lib/Linux64_x64/libNodeMapData_gcc54_v3_3_LUCID.so
    ${PROJECT_SOURCE_DIR}/GenICam/library/lib/Linux64_x64/libXmlParser_gcc54_v3_3_LUCID.so

    ${PROJECT_SOURCE_DIR}/ffmpeg/libavcodec.so
    ${PROJECT_SOURCE_DIR}/ffmpeg/libavformat.so
    ${PROJECT_SOURCE_DIR}/ffmpeg/libavutil.so
    ${PROJECT_SOURCE_DIR}/ffmpeg/libswresample.so
)
set(Arena_LIBS ${Arena_LIBS})

target_link_libraries(rgbd PUBLIC
                    ${Arena_LIBS}
                    ${OpenCV_LIBS}
)

target_include_directories(rgbd PUBLIC
                        "${PROJECT_SOURCE_DIR}/include/Arena"
                        "${PROJECT_SOURCE_DIR}/include/Save"
                        "${PROJECT_SOURCE_DIR}/include/GenTL"
                        "${PROJECT_SOURCE_DIR}/GenICam/library/CPP/include"
)
