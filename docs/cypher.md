# Cypher

### Schema Discovery

List all nodes label, list all relation type

```
> START n=node(*) RETURN distinct labels(n)

> match n-[r]-() return distinct type(r)
```

**UI Way**: Click to Overtab in Neo4j Browser

### Sample 10 entities

```
> MATCH (n:Entity) RETURN n, rand() as random ORDER BY random LIMIT 10
```

### Group By

http://www.markhneedham.com/blog/2013/02/17/neo4jcypher-sql-style-group-by-functionality/

<strong>Graph Algorithms</strong>

<code>shortestPath</code>, <code>dijkstra</code>

```
POST http://localhost:7474/db/data/node/72/paths

Headers
Accept: application/json
Authorization: Basic bmVvNGo6cGFzc3dk

Body
{
  "to" : "http://localhost:7474/db/data/node/77",
  "max_depth" : 5,
  "relationships" : {
    "type" : "FRIEND",
    "direction" : "out"
  },
  "algorithm" : "shortestPath"
}
```

<strong>Graph Analystic</strong>

<code>pagerank</code>, <code>closeness_centrality</code>, <code>betweenness_centrality</code>, <code>triangle_count</code>,
<code>connected_components</code>, <code>strongly_connected_components</code>

