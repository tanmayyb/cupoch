add_subdirectory(cupoch)
if (BUILD_UNIT_TESTS)
    add_subdirectory(tests)
endif ()
if (BUILD_PYTHON_MODULE)
    add_subdirectory(python)
endif ()

install(EXPORT cupochTargets
  FILE cupochTargets.cmake
  NAMESPACE cupoch::
  DESTINATION lib/cmake/cupoch
)

include(CMakePackageConfigHelpers)
write_basic_package_version_file(
  "${CMAKE_CURRENT_BINARY_DIR}/cupochConfigVersion.cmake"
  VERSION ${PROJECT_VERSION}
  COMPATIBILITY AnyNewerVersion
)

configure_package_config_file(
  "${CMAKE_CURRENT_SOURCE_DIR}/cmake/cupochConfig.cmake.in"
  "${CMAKE_CURRENT_BINARY_DIR}/cupochConfig.cmake"
  INSTALL_DESTINATION lib/cmake/cupoch
)

install(FILES
  "${CMAKE_CURRENT_BINARY_DIR}/cupochConfig.cmake"
  "${CMAKE_CURRENT_BINARY_DIR}/cupochConfigVersion.cmake"
  DESTINATION lib/cmake/cupoch
)