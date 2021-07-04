project(python-py2app)

set(p2app_dest libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/py2app)

add_darling_executable(py2app_apptemplate
	py2app/apptemplate/src/main.c
)

add_darling_bundle(py2app_bundletemplate ""
	py2app/bundletemplate/src/main.m
)

target_link_libraries(py2app_bundletemplate
	system
	Foundation
	AppKit
)

install(
	PROGRAMS "$<TARGET_FILE:py2app_apptemplate>"
	DESTINATION "${p2app_dest}/apptemplate/prebuilt"
	RENAME "main"
)

install(
	PROGRAMS "$<TARGET_FILE:py2app_bundletemplate>"
	DESTINATION "${p2app_dest}/bundletemplate/prebuilt"
	RENAME "main"
)

set(py2app_pysrc
	py2app/__init__.py
	py2app/build_app.py
	py2app/create_appbundle.py
	py2app/create_pluginbundle.py
	py2app/decorators.py
	py2app/filters.py
	py2app/script_py2applet.py
	py2app/util.py
)

set(py2app_apptemplate_pysrc
	py2app/apptemplate/__init__.py
	py2app/apptemplate/plist_template.py
	py2app/apptemplate/setup.py
)

set(py2app_apptemplate_lib_pysrc
	py2app/apptemplate/lib/site.py
)

set(py2app_bootstrap_pysrc
	py2app/bootstrap/__init__.py
	py2app/bootstrap/argv_emulation.py
	py2app/bootstrap/argv_inject.py
	py2app/bootstrap/boot_aliasapp.py
	py2app/bootstrap/boot_aliasplugin.py
	py2app/bootstrap/boot_app.py
	py2app/bootstrap/boot_plugin.py
	py2app/bootstrap/chdir_resource.py
	py2app/bootstrap/disable_linecache.py
	py2app/bootstrap/emulate_shell_environment.py
	py2app/bootstrap/import_encodings.py
	py2app/bootstrap/path_inject.py
	py2app/bootstrap/reset_sys_path.py
	py2app/bootstrap/semi_standalone_path.py
	py2app/bootstrap/setup_pkgresource.py
	py2app/bootstrap/site_packages.py
	py2app/bootstrap/system_path_extras.py
	py2app/bootstrap/virtualenv_site_packages.py
	py2app/bootstrap/virtualenv.py
)

set(py2app_bundletemplate_pysrc
	py2app/bundletemplate/__init__.py
	py2app/bundletemplate/plist_template.py
	py2app/bundletemplate/setup.py
)

set(py2app_bundletemplate_lib_pysrc
	py2app/bundletemplate/lib/site.py
)

set(py2app_converters_pysrc
	py2app/converters/__init__.py
	py2app/converters/coredata.py
	py2app/converters/nibfile.py
)

set(py2app_recipes_pysrc
	py2app/recipes/__init__.py
	py2app/recipes/cjkcodecs.py
	py2app/recipes/docutils.py
	py2app/recipes/email.py
	py2app/recipes/matplotlib_prescript.py
	py2app/recipes/matplotlib.py
	py2app/recipes/numpy.py
	py2app/recipes/pydoc.py
	py2app/recipes/pygame.py
	py2app/recipes/pyopengl.py
	py2app/recipes/pyside.py
	py2app/recipes/pyzmq.py
	py2app/recipes/scipy.py
	py2app/recipes/sip.py
	py2app/recipes/virtualenv.py
	py2app/recipes/wx.py
)

set(py2app_recipes_PIL_pysrc
	py2app/recipes/PIL/__init__.py
	py2app/recipes/PIL/prescript.py
)

pyc(py27_py2app
	SOURCES ${py2app_pysrc}
	DESTINATION ${p2app_dest}
)
install(
	FILES ${py2app_pysrc}
	DESTINATION ${p2app_dest}
)

pyc(py27_py2app_apptemplate
	SOURCES ${py2app_apptemplate_pysrc}
	DESTINATION ${p2app_dest}/apptemplate
)
install(
	FILES ${py2app_apptemplate_pysrc}
	DESTINATION ${p2app_dest}/apptemplate
)

pyc(py27_py2app_apptemplate_lib
	SOURCES ${py2app_apptemplate_lib_pysrc}
	DESTINATION ${p2app_dest}/apptemplate/lib
)
install(
	FILES ${py2app_apptemplate_lib_pysrc}
	DESTINATION ${p2app_dest}/apptemplate/lib
)

pyc(py27_py2app_bootstrap
	SOURCES ${py2app_bootstrap_pysrc}
	DESTINATION ${p2app_dest}/bootstrap
)
install(
	FILES ${py2app_bootstrap_pysrc}
	DESTINATION ${p2app_dest}/bootstrap
)

pyc(py27_py2app_bundletemplate
	SOURCES ${py2app_bundletemplate_pysrc}
	DESTINATION ${p2app_dest}/bundletemplate
)
install(
	FILES ${py2app_bundletemplate_pysrc}
	DESTINATION ${p2app_dest}/bundletemplate
)

pyc(py27_py2app_bundletemplate_lib
	SOURCES ${py2app_bundletemplate_lib_pysrc}
	DESTINATION ${p2app_dest}/bundletemplate/lib
)
install(
	FILES ${py2app_bundletemplate_lib_pysrc}
	DESTINATION ${p2app_dest}/bundletemplate/lib
)

pyc(py27_py2app_converters
	SOURCES ${py2app_converters_pysrc}
	DESTINATION ${p2app_dest}/converters
)
install(
	FILES ${py2app_converters_pysrc}
	DESTINATION ${p2app_dest}/converters
)

pyc(py27_py2app_recipes
	SOURCES ${py2app_recipes_pysrc}
	DESTINATION ${p2app_dest}/recipes
)
install(
	FILES ${py2app_recipes_pysrc}
	DESTINATION ${p2app_dest}/recipes
)

pyc(py27_py2app_recipes_PIL
	SOURCES ${py2app_recipes_PIL_pysrc}
	DESTINATION ${p2app_dest}/recipes/PIL
)
install(
	FILES ${py2app_recipes_PIL_pysrc}
	DESTINATION ${p2app_dest}/recipes/PIL
)

install(
	FILES py2app/apptemplate/lib/__error__.sh
	DESTINATION ${p2app_dest}/apptemplate/lib
)

install(
	FILES py2app/apptemplate/src/main.c
	DESTINATION ${p2app_dest}/apptemplate/src
)

install(
	FILES py2app/bundletemplate/lib/__error__.sh
	DESTINATION ${p2app_dest}/bundletemplate/lib
)

install(
	FILES py2app/bundletemplate/src/main.m
	DESTINATION ${p2app_dest}/bundletemplate/src
)

install(
	FILES py2app/recipes/qt.conf
	DESTINATION ${p2app_dest}/recipes
)

install(
	DIRECTORY py2app.egg-info/
	DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/py2app-0.7.3-py2.7.egg-info
)
