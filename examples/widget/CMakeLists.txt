
find_package(Qt6 COMPONENTS Core OpenGLWidgets REQUIRED)

if (ANDROID)
    add_library(qt_imgui_demo_widget SHARED demo-widget.cpp)
else()
    add_executable(qt_imgui_demo_widget demo-widget.cpp)
endif()

target_link_libraries(qt_imgui_demo_widget PUBLIC qt_imgui_widgets implot  Qt6::OpenGLWidgets)

if(ANDROID)
    include(${CMAKE_CURRENT_LIST_DIR}/../../tools/qt-android-cmake/AddQtAndroidApk.cmake)
    add_qt_android_apk(qt_imgui_demo_widget_apk qt_imgui_demo_widget)
endif()
