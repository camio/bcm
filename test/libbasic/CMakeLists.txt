cmake_minimum_required (VERSION 2.8.12)
project(basic)

find_package(BCM)

include(BCMInstallTargets)
include(BCMPackageConfigHelpers)
include(BCMTest)
include(BCMSetupVersion)

bcm_setup_version(VERSION 1.0)

find_package(simple)
add_library(basic main.cpp)
target_link_libraries(basic ${simple_LIBRARIES})

bcm_install_targets(TARGETS basic)
bcm_auto_export(TARGETS basic
    DEPENDS
        PACKAGE simple 1.0
)

bcm_test(NAME basictest SOURCES test.cpp)
target_link_libraries(basictest basic)

