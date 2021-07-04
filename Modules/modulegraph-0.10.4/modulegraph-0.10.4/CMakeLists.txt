project(python-modulegraph)

set(modulegraph_pysrc
	modulegraph/__init__.py
	modulegraph/__main__.py
	modulegraph/_compat.py
	modulegraph/find_modules.py
	modulegraph/modulegraph.py
	modulegraph/util.py
	modulegraph/zipio.py
)

pyc(py27_modulegraph
	SOURCES ${modulegraph_pysrc}
	DESTINATION libexec/darling/System/Library/Frameworks/Python.framework//Versions/2.7/Extras/lib/python/modulegraph
)

install(
	FILES ${modulegraph_pysrc}
	DESTINATION libexec/darling/System/Library/Frameworks/Python.framework//Versions/2.7/Extras/lib/python/modulegraph
)

install(
	DIRECTORY modulegraph.egg-info/
	DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/modulegraph-0.10.4-py2.7.egg-info
)
