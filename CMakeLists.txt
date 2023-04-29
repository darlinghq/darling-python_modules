project(python_modules)

include(CMakeParseArguments)
include(darling_bundle)

function(build_pybundle name)
	cmake_parse_arguments(BUNDLE "FAT;NO_SUFFIX" "PYTHON_VERSION;DESTINATION;OUTPUT_NAME" "SOURCES;DEPENDS" ${ARGN})

	if(NOT BUNDLE_OUTPUT_NAME)
		set(BUNDLE_OUTPUT_NAME "${name}")
	endif()

	if (BUNDLE_NO_SUFFIX)
		set(BUNDLE_SUFFIX "")
	else()
		set(BUNDLE_SUFFIX ".so")
	endif()

	# Apple has removed Python 2.6 support, so disable this codepath
	#
	# For Darling, although we do want to keep compatability with older software,
	# Python 2.6 (and really, Python 2 in general) has been deprecated for so long
	# that it really shouldn't be included anywhere anymore
	#
	# Anyways, if this causes a problem later down the line, import the last Python 2.6 version
	# Apple supported from their open source repo and restore some of the plumbing throughout the various
	# Python-related CMakeLists (in the core Python repo and in these packages too) to make it work

	#if (BUNDLE_PYTHON_VERSION STREQUAL "2.6")
	#	set(suffix "_py26")
	#	include_directories(
	#		${CMAKE_SOURCE_DIR}/src/external/python/2.6/Python-2.6.9/Include
	#		${CMAKE_SOURCE_DIR}/src/external/python/2.6/Python-2.6.9
	#	)
	#elseif (BUNDLE_PYTHON_VERSION STREQUAL "2.7")
	if (BUNDLE_PYTHON_VERSION STREQUAL "2.7")
		set(suffix "_py27")
		include_directories(
			${CMAKE_SOURCE_DIR}/src/external/python/2.7/Python-2.7.16/Include
			${CMAKE_SOURCE_DIR}/src/external/python/2.7/Python-2.7.16
		)
	else()
		message(FATAL_ERROR "Unknown Python version set: ${BUNDLE_PYTHON_VERSION}")
	endif()

	set(full_name "${name}${suffix}")
	add_darling_bundle("${full_name}" "" ${BUNDLE_SOURCES})

	if (BUNDLE_FAT)
		make_fat("${full_name}")
	endif (BUNDLE_FAT)

	set_property(TARGET "${full_name}" APPEND_STRING PROPERTY LINK_FLAGS " -Wl,-undefined,dynamic_lookup ")

	target_link_libraries("${full_name}" system "${BUNDLE_DEPENDS}")
	install(
		PROGRAMS "$<TARGET_FILE:${full_name}>"
		DESTINATION "${BUNDLE_DESTINATION}"
		RENAME "${BUNDLE_OUTPUT_NAME}${BUNDLE_SUFFIX}"
	)
endfunction(build_pybundle)

function(easyinstall python_version package_name package_version)
	set(local_file "${CMAKE_CURRENT_BINARY_DIR}/${package_name}-${package_version}-${python_version}")

	set(EXEPATH "/System/Library/Frameworks/Python.framework/Versions/${python_version}/bin/python${python_version}")
	set(PYTHON_VERSION ${python_version})
	set(PACKAGE_NAME ${package_name})
	set(PACKAGE_VERSION ${package_version})

	configure_file(${CMAKE_SOURCE_DIR}/src/external/python_modules/darling/src/easyinstall.py.in "${local_file}")
	install(PROGRAMS "${local_file}" DESTINATION libexec/darling/usr/bin RENAME "${package_name}-${python_version}")
endfunction(easyinstall)

add_subdirectory(Modules/six-1.12.0/six-1.12.0)
add_subdirectory(Modules/macholib-1.5.1/macholib-1.5.1)
add_subdirectory(Modules/xattr-0.6.4/xattr-0.6.4)
add_subdirectory(Modules/setuptools-41.0.1/setuptools-41.0.1)
if (COMPONENT_dev_gui_common)
	add_subdirectory(Modules/py2app-0.7.3/py2app-0.7.3-noprebuilt)
endif()
add_subdirectory(Modules/altgraph-0.10.2/altgraph-0.10.2)
add_subdirectory(Modules/modulegraph-0.10.4/modulegraph-0.10.4)

#install(FILES Extras-2.6.pth DESTINATION libexec/darling/Library/Python/2.6/site-packages RENAME Extras.pth)
install(FILES darling/src/Extras-2.7.pth DESTINATION libexec/darling/Library/Python/2.7/site-packages RENAME Extras.pth)

