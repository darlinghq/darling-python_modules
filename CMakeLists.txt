project(python_modules)

include(CMakeParseArguments)
include(darling_bundle)

function(build_pybundle name)
	cmake_parse_arguments(BUNDLE "FAT" "PYTHON_VERSION;DESTINATION" "SOURCES" ${ARGN})

	if (BUNDLE_PYTHON_VERSION STREQUAL "2.6")
		set(suffix "_py26")
		include_directories(
			${CMAKE_SOURCE_DIR}/src/external/python/2.6/Python-2.6.9/Include
			${CMAKE_SOURCE_DIR}/src/external/python/2.6/Python-2.6.9
		)
	elseif (BUNDLE_PYTHON_VERSION STREQUAL "2.7")
		set(suffix "_py27")
		include_directories(
			${CMAKE_SOURCE_DIR}/src/external/python/2.7/Python-2.7.10/Include
			${CMAKE_SOURCE_DIR}/src/external/python/2.7/Python-2.7.10
		)
	else()
		message(FATAL_ERROR "Unknown Python version set: ${BUNDLE_PYTHON_VERSION}")
	endif()

	set(full_name "${name}_${suffix}")
	add_darling_bundle("${full_name}" "" ${BUNDLE_SOURCES})

	if (BUNDLE_FAT)
		make_fat("${full_name}")
	endif (BUNDLE_FAT)

	set_property(TARGET "${full_name}" APPEND_STRING PROPERTY LINK_FLAGS " -Wl,-flat_namespace -Wl,-undefined,suppress ")

	target_link_libraries("${full_name}" system)
	install(TARGETS "${full_name}" DESTINATION "${BUNDLE_DESTINATION}")
	install(CODE "execute_process(COMMAND mv ${full_name} ${name}.so WORKING_DIRECTORY ${BUNDLE_DESTINATION})")
endfunction(build_pybundle)

function(easyinstall python_version package_name package_version)
	set(local_file "${CMAKE_CURRENT_BINARY_DIR}/${package_name}-${package_version}-${python_version}")

	set(EXEPATH "/System/Library/Frameworks/Python.framework/Versions/${python_version}/bin/python${python_version}")
	set(PYTHON_VERSION ${python_version})
	set(PACKAGE_NAME ${package_name})
	set(PACKAGE_VERSION ${package_version})

	configure_file(${CMAKE_SOURCE_DIR}/src/external/python_modules/easyinstall.py.in "${local_file}")
	install(PROGRAMS "${local_file}" DESTINATION libexec/darling/usr/bin RENAME "${package_name}-${python_version}")
endfunction(easyinstall)

add_subdirectory(Modules/six-1.4.1/six-1.4.1)
add_subdirectory(Modules/macholib-1.5.1/macholib-1.5.1)
add_subdirectory(Modules/macholib-1.5/macholib-1.5)
add_subdirectory(Modules/xattr-0.6.4/xattr-0.6.4)
add_subdirectory(Modules/setuptools-18.5/setuptools-18.5)

install(FILES Extras-2.6.pth DESTINATION libexec/darling/Library/Python/2.6/site-packages RENAME Extras.pth)
install(FILES Extras-2.7.pth DESTINATION libexec/darling/Library/Python/2.7/site-packages RENAME Extras.pth)

