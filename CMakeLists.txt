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
	set_target_properties("${full_name}" PROPERTIES OUTPUT_NAME "${name}" PREFIX "" SUFFIX ".so")

	target_link_libraries("${full_name}" system)
	install(TARGETS "${full_name}" DESTINATION "${BUNDLE_DESTINATION}")
endfunction(build_pybundle)

add_subdirectory(Modules/six-1.4.1/six-1.4.1)
add_subdirectory(Modules/macholib-1.5.1/macholib-1.5.1)
add_subdirectory(Modules/macholib-1.5/macholib-1.5)
add_subdirectory(Modules/xattr-0.6.4/xattr-0.6.4)

install(FILES Extras-2.6.pth DESTINATION libexec/darling/Library/Python/2.6/site-packages RENAME Extras.pth)
install(FILES Extras-2.7.pth DESTINATION libexec/darling/Library/Python/2.7/site-packages RENAME Extras.pth)

