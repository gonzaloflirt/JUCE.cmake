# This file was generated by Jucer2Reprojucer from BinaryBuilder.jucer

cmake_minimum_required(VERSION 3.4)


list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_LIST_DIR}/../../../../../cmake")
include(Reprojucer)


if(NOT DEFINED BinaryBuilder_jucer_FILE)
  message(FATAL_ERROR "BinaryBuilder_jucer_FILE must be defined")
endif()

get_filename_component(BinaryBuilder_jucer_FILE
  "${BinaryBuilder_jucer_FILE}" ABSOLUTE
  BASE_DIR "${CMAKE_BINARY_DIR}"
)


jucer_project_begin(
  PROJECT_FILE "${BinaryBuilder_jucer_FILE}"
  PROJECT_ID "3t6YqETY1"
)

jucer_project_settings(
  PROJECT_NAME "BinaryBuilder"
  PROJECT_VERSION "1.0.0"
  # COMPANY_NAME
  # COMPANY_WEBSITE
  # COMPANY_EMAIL
  PROJECT_TYPE "Console Application"
  BUNDLE_IDENTIFIER "com.rawmaterialsoftware.binarybuilder"
  BINARYDATACPP_SIZE_LIMIT "Default"
  # BINARYDATA_NAMESPACE
  # PREPROCESSOR_DEFINITIONS
)

jucer_project_files("BinaryBuilder/Source"
# Compile   Xcode     Binary
#           Resource  Resource
  x         .         .         "Source/Main.cpp"
)

jucer_project_module(
  juce_core
  PATH "../../modules"
  # JUCE_FORCE_DEBUG
  # JUCE_LOG_ASSERTIONS
  # JUCE_CHECK_MEMORY_LEAKS
  # JUCE_DONT_AUTOLINK_TO_WIN32_LIBRARIES
  # JUCE_INCLUDE_ZLIB_CODE
  # JUCE_USE_CURL
  # JUCE_CATCH_UNHANDLED_EXCEPTIONS
  # JUCE_ALLOW_STATIC_NULL_VARIABLES
)

jucer_export_target(
  "Xcode (MacOSX)"
  # EXTRA_PREPROCESSOR_DEFINITIONS
  # EXTRA_COMPILER_FLAGS
  # EXTRA_LINKER_FLAGS
  # EXTERNAL_LIBRARIES_TO_LINK
  ICON_SMALL "<None>"
  ICON_LARGE "<None>"
  # EXTRA_FRAMEWORKS
  # PREBUILD_SHELL_SCRIPT
  # POSTBUILD_SHELL_SCRIPT
)

jucer_export_target_configuration(
  "Xcode (MacOSX)"
  NAME "Debug"
  # HEADER_SEARCH_PATHS
  # PREPROCESSOR_DEFINITIONS
  # OSX_BASE_SDK_VERSION
  # OSX_DEPLOYMENT_TARGET
  OSX_ARCHITECTURE "Use Default"
  CXX_LANGUAGE_STANDARD "Use Default"
)

jucer_export_target_configuration(
  "Xcode (MacOSX)"
  NAME "Release"
  # HEADER_SEARCH_PATHS
  # PREPROCESSOR_DEFINITIONS
  # OSX_BASE_SDK_VERSION
  # OSX_DEPLOYMENT_TARGET
  OSX_ARCHITECTURE "Use Default"
  CXX_LANGUAGE_STANDARD "Use Default"
)

jucer_export_target(
  "Linux Makefile"
  # EXTRA_PREPROCESSOR_DEFINITIONS
  # EXTRA_COMPILER_FLAGS
  # EXTRA_LINKER_FLAGS
  # EXTERNAL_LIBRARIES_TO_LINK
  ICON_SMALL "<None>"
  ICON_LARGE "<None>"
  # CXX_STANDARD_TO_USE
)

jucer_export_target_configuration(
  "Linux Makefile"
  NAME "Debug"
  # HEADER_SEARCH_PATHS
  # PREPROCESSOR_DEFINITIONS
)

jucer_export_target_configuration(
  "Linux Makefile"
  NAME "Release"
  # HEADER_SEARCH_PATHS
  # PREPROCESSOR_DEFINITIONS
)

jucer_project_end()
