include_directories(
    ${CMAKE_BINARY_DIR}/src
    ${CMAKE_BINARY_DIR}/src/gsettings
    ${CMAKE_BINARY_DIR}/src/gsettings/Hawaii
)

set(SOURCES
    plugin.cpp
    qmlgsettings.cpp
    qmlgsettingsschema.cpp
)

add_library(gsettingsplugin SHARED ${SOURCES})
target_link_libraries(gsettingsplugin
                      Qt5::Core
                      Qt5::Gui
                      Qt5::Qml
                      Qt5::Quick
                      Hawaii::GSettings)

install(FILES qmldir plugins.qmltypes
    DESTINATION ${QML_INSTALL_DIR}/Hawaii/GSettings)
install(TARGETS gsettingsplugin
    DESTINATION ${QML_INSTALL_DIR}/Hawaii/GSettings)
