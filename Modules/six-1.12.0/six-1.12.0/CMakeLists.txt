project(python-six)

pyc("py27_six" SOURCES six.py DESTINATION libexec/darling/System/Library/Frameworks/Python.framework//Versions/2.7/Extras/lib/python)
install(FILES six.py DESTINATION libexec/darling/System/Library/Frameworks/Python.framework//Versions/2.7/Extras/lib/python)

install(DIRECTORY six.egg-info/ DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/six-1.12.0-py2.7.egg-info)

# update this if you want to add back Python 2.6 support
#install(FILES ${eggfiles} DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.6/Extras/lib/python/six-1.4.1-py2.6.egg-info)
