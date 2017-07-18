project(python-six)

pyc("py27_six" SOURCES six.py DESTINATION libexec/darling/System/Library/Frameworks/Python.framework//Versions/2.7/Extras/lib/python)
install(FILES six.py DESTINATION libexec/darling/System/Library/Frameworks/Python.framework//Versions/2.7/Extras/lib/python)

