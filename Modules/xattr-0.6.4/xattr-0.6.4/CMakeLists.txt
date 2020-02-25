project(python-xattr)

set(xattr_src xattr/_xattr.c)
set(xattr_pysrc
	xattr/constants.py
	xattr/__init__.py
	xattr/tool.py
)

build_pybundle(_xattr
	PYTHON_VERSION "2.6"
	FAT
	SOURCES ${xattr_src}
	DESTINATION "libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.6/Extras/lib/python/xattr"
)

build_pybundle(_xattr
	PYTHON_VERSION "2.7"
	FAT
	SOURCES ${xattr_src}
	DESTINATION "libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/xattr"
)

install(FILES ${xattr_pysrc} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.6/Extras/lib/python/xattr)

install(FILES ${xattr_pysrc} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/xattr)

easyinstall("2.6" "xattr" "0.6.4")
easyinstall("2.7" "xattr" "0.6.4")

file(WRITE ${CMAKE_CURRENT_BINARY_DIR}/entry_points.txt "[console_scripts]\nxattr = xattr.tool:main\n")
file(WRITE ${CMAKE_CURRENT_BINARY_DIR}/top_level.txt "xattr\n")

set(eggfiles
	CHANGES.txt
	INSTALLING.txt
	LICENSE.txt
	PKG-INFO
	README.txt
	${CMAKE_CURRENT_BINARY_DIR}/entry_points.txt
	${CMAKE_CURRENT_BINARY_DIR}/top_level.txt
)
INSTALL(FILES ${eggfiles} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/xattr-0.6.4-py2.7.egg-info)
INSTALL(FILES ${eggfiles} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.6/Extras/lib/python/xattr-0.6.4-py2.6.egg-info)
