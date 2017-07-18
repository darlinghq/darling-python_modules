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
