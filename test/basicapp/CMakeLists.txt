cmake_minimum_required (VERSION 2.8.12)
project(basicapp)

find_package(BCM)

include(BCMInstallTargets)
include(BCMPackageConfigHelpers)
include(BCMTest)
include(BCMSetupVersion)

bcm_setup_version(VERSION 1.0)

find_package(simple)
add_executable(basicapp main.cpp)
target_link_libraries(basicapp simple)

bcm_install_targets(TARGETS basicapp)
bcm_auto_export(TARGETS basicapp)
# install(TARGETS basicapp DESTINATION bin)

bcm_test(NAME basciapptest SOURCES main.cpp)
target_link_libraries(basciapptest simple)

