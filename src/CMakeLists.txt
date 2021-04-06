### Sets QT_INSTALL_QML to the directory where QML Plugins should be installed
function(FindQtInstallQml)
    find_program(QMAKE NAMES qmake-qt5 qmake)
    if(NOT QMAKE)
    message(FATAL_ERROR "qmake not found")
    endif()
    execute_process(
        COMMAND ${QMAKE} -query QT_INSTALL_QML
        OUTPUT_VARIABLE PROC_RESULT
        OUTPUT_STRIP_TRAILING_WHITESPACE
    )
    set(QT_INSTALL_QML ${PROC_RESULT} PARENT_SCOPE)
endfunction()


set(SRC
    sortfiltermodel.cpp
    plugin.cpp)

set(HEADERS
    sortfiltermodel.h)

add_library(nemosortfiltermodel SHARED ${SRC})

target_link_libraries(nemosortfiltermodel
    Qt5::Core
    Qt5::Qml 
    Qt5::Quick)

FindQtInstallQml()

install(FILES qmldir DESTINATION ${QT_INSTALL_QML}/org/nemomobile/sortfiltermodel/)
install(TARGETS nemosortfiltermodel DESTINATION ${QT_INSTALL_QML}/org/nemomobile/sortfiltermodel/)