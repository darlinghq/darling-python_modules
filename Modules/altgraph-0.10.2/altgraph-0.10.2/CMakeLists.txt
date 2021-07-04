project(python-altgraph)

set(altgraph_pysrc
	altgraph/__init__.py
	altgraph/Dot.py
	altgraph/Graph.py
	altgraph/GraphAlgo.py
	altgraph/GraphStat.py
	altgraph/GraphUtil.py
	altgraph/ObjectGraph.py
)

pyc(py27_altgraph
	SOURCES ${altgraph_pysrc}
	DESTINATION libexec/darling/System/Library/Frameworks/Python.framework//Versions/2.7/Extras/lib/python/altgraph
)

install(
	FILES ${altgraph_pysrc}
	DESTINATION libexec/darling/System/Library/Frameworks/Python.framework//Versions/2.7/Extras/lib/python/altgraph
)

install(
	DIRECTORY altgraph.egg-info/
	DESTINATION libexec/darling/System/Library/Frameworks/Python.framework/Versions/2.7/Extras/lib/python/altgraph-0.10.2-py2.7.egg-info
)
