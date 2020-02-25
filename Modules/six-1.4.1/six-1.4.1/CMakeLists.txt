project(python-six)

pyc("py27_six" SOURCES six.py DESTINATION libexec/darling/System/Library/Frameworks/Python.framework//Versions/2.7/Extras/lib/python)
install(FILES six.py DESTINATION libexec/darling/System/Library/Frameworks/Python.framework//Versions/2.7/Extras/lib/python)

set(eggfiles
	PKG-INFO
	README
)
INSTALL(FILES ${eggfiles} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/six-1.4.1-py2.7.egg-info)
INSTALL(FILES ${eggfiles} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.6/Extras/lib/python/six-1.4.1-py2.6.egg-info)
