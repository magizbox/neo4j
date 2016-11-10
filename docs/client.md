In this article you will know how to connect to neo4j database from python.

# Python Client

We can use Py2neo to connect to neo4j from python.

[Py2neo](http://py2neo.org/2.0/) is a client library and comprehensive toolkit for working with Neo4j from within Python applications and from the command line. The core library has no external dependencies and has been carefully designed to be easy and intuitive to use.

Snippets to connect, create, add nodes, add relationship and update property

```python
from py2neo import authenticate, Graph, Node, Relationship
# connect to graph
authenticate("localhost:7474", "neo4j", "passwd")
graph = Graph("http://localhost:7474/db/data/")

# create unique
graph.schema.create_uniqueness_constraint('Person', 'name')

# add nodes
graph.create(Node.cast('Person', {"name": "Alice"}))
graph.create(Node.cast('Person', {"name": "Bob"}))

# add relationship
source = graph.merge_one("Person", "name", "Alice")
target = graph.merge_one("Person", "name", "Bob")
graph.create_unique(Relationship(source, "FRIEND", target))

# update property
alice = graph.merge_one("Person", "name", "Alice")
alice["age"] = 30
alice.push()
```

