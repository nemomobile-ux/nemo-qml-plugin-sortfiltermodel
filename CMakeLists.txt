cmake_minimum_required(VERSION 3.5.0)

project(nemosortfiltermodel
    VERSION 0.1
    DESCRIPTION "Provides QML features of class QSortFilterModel")

set(CMAKE_AUTOMOC ON)

set(CMAKE_INCLUDE_CURRENT_DIR ON)
include(FeatureSummary)
include(GNUInstallDirs)

set(QT_MIN_VERSION "6.0.0")
find_package(Qt6 COMPONENTS Core Qml Quick REQUIRED)

add_subdirectory(src)

feature_summary(WHAT PACKAGES_FOUND PACKAGES_NOT_FOUND FATAL_ON_MISSING_REQUIRED_PACKAGES)
