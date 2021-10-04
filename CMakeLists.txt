cmake_minimum_required(VERSION 3.2)

project(gyro-sms)

install(FILES
    ${CMAKE_INSTALL_PREFIX}/bin/gyrod
    ${CMAKE_INSTALL_PREFIX}/bin/gyro-wallet-cli
    ${CMAKE_INSTALL_PREFIX}/bin/gyro-wallet-sms
    DESTINATION /usr/bin
  	PERMISSIONS OWNER_EXECUTE OWNER_WRITE OWNER_READ GROUP_READ GROUP_EXECUTE WORLD_READ WORLD_EXECUTE
)

install(FILES
    ${CMAKE_INSTALL_PREFIX}/lib/libzyre.so
    ${CMAKE_INSTALL_PREFIX}/lib/libzyre.so.2
    ${CMAKE_INSTALL_PREFIX}/lib/libzyre.so.2.0.1
    DESTINATION /usr/lib
  	PERMISSIONS OWNER_EXECUTE OWNER_WRITE OWNER_READ GROUP_READ GROUP_EXECUTE WORLD_READ WORLD_EXECUTE
)

install(FILES
    gyro.conf
    DESTINATION /var/lib/gyro
)

set(DEB_PACKAGE_NAME ${CMAKE_PROJECT_NAME})
set(DEB_PACKAGE_VERSION "0.1.0")
set(DEB_PACKAGE_COMMIT "ubuntu-20.04")
set(DEB_PACKAGE_SECTION "internet")
set(DEB_PACKAGE_DEPENDS "libc6, libsodium23, libssl1.1, libhidapi-libusb0, libqt5gui5, libqt5network5, libx11-6, libqt5core5a, libstdc++6, libqt5qml5, libzmq5, libqt5widgets5, libreadline8, libunbound8, libqt5quick5, libgcrypt20, libgcc-s1, libczmq4, qml-module-qtgraphicaleffects, qml-module-qtquick-layouts, qml-module-qtquick-window2, qml-module-qtquick2, qml-module-qtgraphicaleffects, qml-module-qtquick-controls, qml-module-qtquick-layouts, qml-module-qtquick-window2, qml-module-qtquick2, qml-module-qtquick-privatewidgets, qml-module-qtquick-dialogs, qml-module-qtquick-privatewidgets, libqt5quicktemplates2-5, qml-module-qtquick-templates2, qml-module-qt-labs-settings, qml-module-qt-labs-folderlistmodel, libqt5quickcontrols2-5, qml-module-qtquick-controls2, qml-module-qtquick-xmllistmodel")
set(DEB_PACKAGE_DESRCIPTION "gyro-sms")
set(DEB_PACKAGE_MAINTAINER "Staroy <staroy@pm.me>")
set(CPACK_DEBIAN_PACKAGE_CONTROL_EXTRA "${CMAKE_CURRENT_SOURCE_DIR}/postinst/postinst")

include(deb_packaging.cmake)
