project(python-setuptools)

set(setuptools_src
	setuptools/archive_util.py
	setuptools/compat.py
	setuptools/depends.py
	setuptools/dist.py
	setuptools/extension.py
	setuptools/__init__.py
	setuptools/lib2to3_ex.py
	setuptools/msvc9_support.py
	setuptools/package_index.py
	setuptools/py26compat.py
	setuptools/py27compat.py
	setuptools/py31compat.py
	setuptools/sandbox.py
	setuptools/site-patch.py
	setuptools/ssl_support.py
	setuptools/unicode_utils.py
	setuptools/utils.py
	setuptools/version.py
	setuptools/windows_support.py
)
set(setuptools_command_src
	setuptools/command/alias.py
	setuptools/command/bdist_egg.py
	setuptools/command/bdist_rpm.py
	setuptools/command/bdist_wininst.py
	setuptools/command/build_ext.py
	setuptools/command/build_py.py
	setuptools/command/develop.py
	setuptools/command/easy_install.py
	setuptools/command/egg_info.py
	setuptools/command/__init__.py
	setuptools/command/install_egg_info.py
	setuptools/command/install_lib.py
	setuptools/command/install.py
	setuptools/command/install_scripts.py
	setuptools/command/register.py
	setuptools/command/rotate.py
	setuptools/command/saveopts.py
	setuptools/command/sdist.py
	setuptools/command/setopt.py
	setuptools/command/test.py
	setuptools/command/upload_docs.py
)

set(setuptools_tmpl
	"setuptools/script (dev).tmpl"
	setuptools/script.tmpl
)

set(pkgresources_src
	pkg_resources/__init__.py
)
set(pkgresources_vendor_src
	pkg_resources/_vendor/__init__.py
)
set(pkgresources_vendorp_src
	pkg_resources/_vendor/packaging/__about__.py
	pkg_resources/_vendor/packaging/_compat.py
	pkg_resources/_vendor/packaging/__init__.py
	pkg_resources/_vendor/packaging/specifiers.py
	pkg_resources/_vendor/packaging/_structures.py
	pkg_resources/_vendor/packaging/version.py
)

pyc("py27_setuptools" SOURCES ${setuptools_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/setuptools)
pyc("py27_setuptools_command" SOURCES ${setuptools_command_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/setuptools/command)
install(FILES ${setuptools_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/setuptools)
install(FILES ${setuptools_command_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/setuptools/command)

pyc("py26_setuptools" SOURCES ${setuptools_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.6/Extras/lib/python/setuptools)
pyc("py26_setuptools_command" SOURCES ${setuptools_command_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.6/Extras/lib/python/setuptools/command)
install(FILES ${setuptools_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.6/Extras/lib/python/setuptools)
install(FILES ${setuptools_command_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.6/Extras/lib/python/setuptools/command)

pyc("py26_pkgr" SOURCES ${pkgresources_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.6/Extras/lib/python/pkg_resources)
pyc("py26_pkgr_vendor" SOURCES ${pkgresources_vendor_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.6/Extras/lib/python/pkg_resources/_vendor/packaging)
pyc("py26_pkgr_vendorp" SOURCES ${pkgresources_vendorp_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.6/Extras/lib/python/pkg_resources/_vendor)
install(FILES ${pkgresources_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.6/Extras/lib/python/pkg_resources)
install(FILES ${pkgresources_vendor_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.6/Extras/lib/python/pkg_resources/_vendor)
install(FILES ${pkgresources_vendorp_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.6/Extras/lib/python/pkg_resources/_vendor/packaging)

pyc("py27_pkgr" SOURCES ${pkgresources_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/pkg_resources)
pyc("py27_pkgr_vendor" SOURCES ${pkgresources_vendor_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/pkg_resources/_vendor/packaging)
pyc("py27_pkgr_vendorp" SOURCES ${pkgresources_vendorp_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/pkg_resources/_vendor)
install(FILES ${pkgresources_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/pkg_resources)
install(FILES ${pkgresources_vendor_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/pkg_resources/_vendor)
install(FILES ${pkgresources_vendorp_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/pkg_resources/_vendor/packaging)

INSTALL(DIRECTORY setuptools.egg-info/ DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/setuptools-18.5-py2.7.egg-info)
INSTALL(DIRECTORY setuptools.egg-info/ DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.6/Extras/lib/python/setuptools-18.5-py2.6.egg-info)
