project(python-macholib-py27)

set(macholib_src
	macholib/_cmdline.py
	macholib/dyld.py
	macholib/dylib.py
	macholib/framework.py
	macholib/__init__.py
	macholib/itergraphreport.py
	macholib/macho_dump.py
	macholib/macho_find.py
	macholib/MachOGraph.py
	macholib/mach_o.py
	macholib/MachO.py
	macholib/macho_standalone.py
	macholib/MachOStandalone.py
	macholib/__main__.py
	macholib/ptypes.py
	macholib/SymbolTable.py
	macholib/util.py
)

pyc("py27_macholib" SOURCES ${macholib_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/macholib)
install(FILES ${macholib_src} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/macholib)

set(eggfiles
	PKG-INFO
	README.txt
)
INSTALL(FILES ${eggfiles} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/macholib-1.5.1-py2.7.egg-info)
INSTALL(FILES ${eggfiles} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.6/Extras/lib/python/macholib-1.5.1-py2.6.egg-info)
