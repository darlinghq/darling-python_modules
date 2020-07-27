project(python-setuptools)

set(setuptools_src
	setuptools/__init__.py
	setuptools/_deprecation_warning.py
	setuptools/archive_util.py
	setuptools/build_meta.py
	setuptools/config.py
	setuptools/dep_util.py
	setuptools/depends.py
	setuptools/dist.py
	setuptools/extension.py
	setuptools/glibc.py
	setuptools/glob.py
	setuptools/launch.py
	setuptools/lib2to3_ex.py
	setuptools/monkey.py
	setuptools/msvc.py
	setuptools/namespaces.py
	setuptools/package_index.py
	setuptools/pep425tags.py
	setuptools/py27compat.py
	setuptools/py31compat.py
	setuptools/py33compat.py
	setuptools/sandbox.py
	setuptools/site-patch.py
	setuptools/ssl_support.py
	setuptools/unicode_utils.py
	setuptools/version.py
	setuptools/wheel.py
	setuptools/windows_support.py
)

set(setuptools_vendor_src
	setuptools/_vendor/__init__.py
	setuptools/_vendor/pyparsing.py
	setuptools/_vendor/six.py
)

set(setuptools_vendor_packaging_src
	setuptools/_vendor/packaging/__about__.py
	setuptools/_vendor/packaging/__init__.py
	setuptools/_vendor/packaging/_compat.py
	setuptools/_vendor/packaging/_structures.py
	setuptools/_vendor/packaging/markers.py
	setuptools/_vendor/packaging/requirements.py
	setuptools/_vendor/packaging/specifiers.py
	setuptools/_vendor/packaging/utils.py
	setuptools/_vendor/packaging/version.py
)

set(setuptools_extern_src
	setuptools/extern/__init__.py
)

set(setuptools_command_src
	setuptools/command/__init__.py
	setuptools/command/alias.py
	setuptools/command/bdist_egg.py
	setuptools/command/bdist_rpm.py
	setuptools/command/bdist_wininst.py
	setuptools/command/build_clib.py
	setuptools/command/build_ext.py
	setuptools/command/build_py.py
	setuptools/command/develop.py
	setuptools/command/dist_info.py
	setuptools/command/easy_install.py
	setuptools/command/egg_info.py
	setuptools/command/install_egg_info.py
	setuptools/command/install_lib.py
	setuptools/command/install_scripts.py
	setuptools/command/install.py
	setuptools/command/py36compat.py
	setuptools/command/register.py
	setuptools/command/rotate.py
	setuptools/command/saveopts.py
	setuptools/command/sdist.py
	setuptools/command/setopt.py
	setuptools/command/test.py
	setuptools/command/upload_docs.py
	setuptools/command/upload.py
)

set(pkgresources_src
	pkg_resources/__init__.py
	pkg_resources/py31compat.py
)

set(pkgresources_extern_src
	pkg_resources/extern/__init__.py
)

set(pkgresources_vendor_src
	pkg_resources/_vendor/__init__.py
	pkg_resources/_vendor/appdirs.py
	pkg_resources/_vendor/pyparsing.py
	pkg_resources/_vendor/six.py
)

set(pkgresources_vendor_packaging_src
	pkg_resources/_vendor/packaging/__about__.py
	pkg_resources/_vendor/packaging/__init__.py
	pkg_resources/_vendor/packaging/_compat.py
	pkg_resources/_vendor/packaging/_structures.py
	pkg_resources/_vendor/packaging/markers.py
	pkg_resources/_vendor/packaging/requirements.py
	pkg_resources/_vendor/packaging/specifiers.py
	pkg_resources/_vendor/packaging/utils.py
	pkg_resources/_vendor/packaging/version.py
)

pyc("py27_setuptools" SOURCES ${setuptools_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/setuptools)
pyc("py27_setuptools_command" SOURCES ${setuptools_command_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/setuptools/command)
pyc("py27_setuptools_vendor" SOURCES ${setuptools_vendor_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/setuptools/_vendor)
pyc("py27_setuptools_vendor_packaging" SOURCES ${setuptools_vendor_packaging_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/setuptools/_vendor/packaging)
pyc("py27_setuptools_extern" SOURCES ${setuptools_extern_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/setuptools/extern)

install(FILES ${setuptools_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/setuptools)
install(FILES ${setuptools_command_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/setuptools/command)
install(FILES ${setuptools_vendor_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/setuptools/_vendor)
install(FILES ${setuptools_vendor_packaging_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/setuptools/_vendor/packaging)
install(FILES ${setuptools_extern_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/setuptools/extern)

pyc("py27_pkgresources" SOURCES ${pkgresources_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/pkg_resources)
pyc("py27_pkgresources_vendor" SOURCES ${pkgresources_vendor_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/pkg_resources/_vendor)
pyc("py27_pkgresources_vendor_packaging" SOURCES ${pkgresources_vendor_packaging_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/pkg_resources/_vendor/packaging)
pyc("py27_pkgresources_extern" SOURCES ${pkgresources_extern_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/pkg_resources/extern)

install(FILES ${pkgresources_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/pkg_resources)
install(FILES ${pkgresources_vendor_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/pkg_resources/_vendor)
install(FILES ${pkgresources_vendor_packaging_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/pkg_resources/_vendor/packaging)
install(FILES ${pkgresources_extern_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/pkg_resources/extern)

install(DIRECTORY setuptools.egg-info/ DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/setuptools-41.0.1-py2.7.egg-info)

# update this if you want to add back Python 2.6 support

#pyc("py26_setuptools" SOURCES ${setuptools_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.6/Extras/lib/python/setuptools)
#pyc("py26_setuptools_command" SOURCES ${setuptools_command_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.6/Extras/lib/python/setuptools/command)
#install(FILES ${setuptools_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.6/Extras/lib/python/setuptools)
#install(FILES ${setuptools_command_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.6/Extras/lib/python/setuptools/command)

#pyc("py26_pkgr" SOURCES ${pkgresources_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.6/Extras/lib/python/pkg_resources)
#pyc("py26_pkgr_vendor" SOURCES ${pkgresources_vendor_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.6/Extras/lib/python/pkg_resources/_vendor/packaging)
#pyc("py26_pkgr_vendorp" SOURCES ${pkgresources_vendorp_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.6/Extras/lib/python/pkg_resources/_vendor)
#install(FILES ${pkgresources_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.6/Extras/lib/python/pkg_resources)
#install(FILES ${pkgresources_vendor_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.6/Extras/lib/python/pkg_resources/_vendor)
#install(FILES ${pkgresources_vendorp_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.6/Extras/lib/python/pkg_resources/_vendor/packaging)
#install(DIRECTORY setuptools.egg-info/ DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.6/Extras/lib/python/setuptools-18.5-py2.6.egg-info)
