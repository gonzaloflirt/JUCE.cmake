# Copyright (c) 2016 Alain Martin
#
# This file is part of JUCE.cmake.
#
# JUCE.cmake is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# JUCE.cmake is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with JUCE.cmake.  If not, see <http://www.gnu.org/licenses/>.

cmake_minimum_required(VERSION 3.4)


list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_LIST_DIR}/../../cmake")
include(Reprojucer)


if(NOT DEFINED Projucer_jucer_FILE)
  message(FATAL_ERROR "Projucer_jucer_FILE must be defined")
endif()

get_filename_component(Projucer_jucer_FILE
  "${Projucer_jucer_FILE}" ABSOLUTE
  BASE_DIR "${CMAKE_BINARY_DIR}"
)

if(NOT EXISTS "${Projucer_jucer_FILE}")
  message(FATAL_ERROR "No such file: ${Projucer_jucer_FILE}")
endif()

get_filename_component(Projucer_jucer_DIR
  "${Projucer_jucer_FILE}" DIRECTORY
)

file(COPY "${Projucer_jucer_DIR}/Source/jucer_Headers.h"
  DESTINATION "${CMAKE_CURRENT_LIST_DIR}/Source"
)

file(COPY
  "${Projucer_jucer_DIR}/Source/Project Saving/jucer_ResourceFile.cpp"
  "${Projucer_jucer_DIR}/Source/Project Saving/jucer_ResourceFile.h"
  DESTINATION "${CMAKE_CURRENT_LIST_DIR}/Source/Project Saving"
)

file(COPY
  "${Projucer_jucer_DIR}/Source/Utility/jucer_CodeHelpers.cpp"
  "${Projucer_jucer_DIR}/Source/Utility/jucer_CodeHelpers.h"
  "${Projucer_jucer_DIR}/Source/Utility/jucer_FileHelpers.cpp"
  "${Projucer_jucer_DIR}/Source/Utility/jucer_FileHelpers.h"
  "${Projucer_jucer_DIR}/Source/Utility/jucer_MiscUtilities.cpp"
  "${Projucer_jucer_DIR}/Source/Utility/jucer_MiscUtilities.h"
  DESTINATION "${CMAKE_CURRENT_LIST_DIR}/Source/Utility"
)


jucer_project_begin()

jucer_project_settings(
  PROJECT_NAME "BinaryDataBuilder"
  PROJECT_VERSION "1.0.0"
  PROJECT_TYPE "Console Application"
)

jucer_project_files("BinaryDataBuilder"
  x . . "${CMAKE_CURRENT_LIST_DIR}/main.cpp"
)

jucer_project_files("BinaryDataBuilder/Source"
  x . . "${CMAKE_CURRENT_LIST_DIR}/Source/Project Saving/jucer_ResourceFile.cpp"
  x . . "${CMAKE_CURRENT_LIST_DIR}/Source/Utility/jucer_CodeHelpers.cpp"
  x . . "${CMAKE_CURRENT_LIST_DIR}/Source/Utility/jucer_FileHelpers.cpp"
  x . . "${CMAKE_CURRENT_LIST_DIR}/Source/Utility/jucer_MiscUtilities.cpp"
)

jucer_project_module(
  juce_core
  PATH "${Projucer_jucer_DIR}/../../modules"
)

jucer_project_module(
  juce_cryptography
  PATH "${Projucer_jucer_DIR}/../../modules"
)

jucer_project_module(
  juce_data_structures
  PATH "${Projucer_jucer_DIR}/../../modules"
)

jucer_project_module(
  juce_events
  PATH "${Projucer_jucer_DIR}/../../modules"
)

jucer_project_module(
  juce_graphics
  PATH "${Projucer_jucer_DIR}/../../modules"
)

jucer_project_module(
  juce_gui_basics
  PATH "${Projucer_jucer_DIR}/../../modules"
)

jucer_project_module(
  juce_gui_extra
  PATH "${Projucer_jucer_DIR}/../../modules"
)

jucer_export_target(
  "Xcode (MacOSX)"
)

jucer_export_target(
  "Visual Studio 2015"
)

jucer_export_target(
  "Visual Studio 2013"
)

jucer_export_target(
  "Linux Makefile"
)

jucer_project_end()


install(TARGETS BinaryDataBuilder DESTINATION "BinaryDataBuilder")
