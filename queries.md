
---

# Starter `queries.md`

```md
# Sample SPARQL Queries

## Query 1 — Subclass-aware query

This query returns all trails, including instances of subclasses such as `HikingTrail`.

```sparql
PREFIX : <http://example.org/jordan-trails/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>

SELECT ?trail ?name
WHERE {
  ?trail a/rdfs:subClassOf* :Trail ;
         skos:prefLabel ?name .
}
ORDER BY ?trail


PREFIX : <http://example.org/jordan-trails/>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>

SELECT ?trail ?trailName ?regionLabel
WHERE {
  ?trail :locatedIn ?region ;
         skos:prefLabel ?trailName .

  ?region (skos:prefLabel|skos:altLabel) ?regionLabel .

  FILTER(LCASE(STR(?regionLabel)) = "dead sea" ||
         LCASE(STR(?regionLabel)) = "salt sea")
}
ORDER BY ?trail


PREFIX : <http://example.org/jordan-trails/>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>

SELECT ?trail ?name ?difficultyName ?distance
WHERE {
  ?trail a :HikingTrail ;
         skos:prefLabel ?name ;
         :hasDifficulty ?difficulty .

  ?difficulty skos:prefLabel ?difficultyName .

  OPTIONAL {
    ?trail :distanceKm ?distance .
  }
}
ORDER BY ?trail