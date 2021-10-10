cmake_minimum_required(VERSION 3.12)

project(warnings-viewer)

find_package(Qt5Widgets REQUIRED)

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_INCLUDE_CURRENT_DIR ON)

qt5_wrap_ui(ui_mainwindow.h mainwindow.ui)
qt5_wrap_ui(ui_settings.h settings.ui)
qt5_add_resources(RESOURCES resources.qrc)

set(SOURCE_FILES
    clazychecks.cpp
    main.cpp
    mainwindow.cpp
    settings.cpp
    settingswindow.cpp
    tab.cpp
    warning.h
    warningmodel.cpp
    warningproxymodel.cpp
    warningtypefilterproxymodel.cpp

    ui_mainwindow.h
    ui_settings.h

    ${RESOURCES}
)

add_executable(warnings-viewer ${SOURCE_FILES})

target_link_libraries(warnings-viewer PRIVATE Qt5::Widgets)

target_compile_options(warnings-viewer PRIVATE -Wall -Wextra)
