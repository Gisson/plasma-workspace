add_subdirectory(tests)

add_library(kio_desktop MODULE kio_desktop.cpp)

target_link_libraries(kio_desktop Qt5::DBus Qt5::Gui KF5::KIOCore)

set_target_properties(kio_desktop PROPERTIES OUTPUT_NAME "desktop")

install(TARGETS kio_desktop DESTINATION ${PLUGIN_INSTALL_DIR}/kf5/kio)

########### next target ###############

add_library(desktopnotifier MODULE desktopnotifier.cpp)
kcoreaddons_desktop_to_json(desktopnotifier desktopnotifier.desktop)
target_link_libraries(desktopnotifier KF5::KIOCore KF5::DBusAddons)

install(TARGETS desktopnotifier DESTINATION ${PLUGIN_INSTALL_DIR}/kf5/kded)

########### install files ###############

install( FILES desktop.protocol  DESTINATION  ${SERVICES_INSTALL_DIR} )

install(FILES directory.desktop directory.trash DESTINATION ${DATA_INSTALL_DIR}/kio_desktop)
install(FILES Home.desktop DESTINATION ${DATA_INSTALL_DIR}/kio_desktop/DesktopLinks)
