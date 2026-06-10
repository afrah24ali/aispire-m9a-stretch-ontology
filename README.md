# aispire-m9a-stretch-ontology

## Domain

This ontology describes a small hiking trail directory in Jordan. I chose this domain because it is simple, familiar, and easy to model with RDF classes and relationships.

## Entity Types and Relationships

Classes:

- `Trail`: the general class for any trail.
- `HikingTrail`: a subclass of `Trail`.
- `Terrain`: the physical type of land, such as forest or canyon.
- `Region`: the location of the trail.
- `Difficulty`: the difficulty level of the trail.

Relationships:

- A trail is located in a region using `:locatedIn`.
- A trail has a terrain type using `:hasTerrain`.
- A trail has a difficulty level using `:hasDifficulty`.
- Some trails have a distance using `:distanceKm`.

## Modeling Decision

I modeled `HikingTrail` as a subclass of `Trail` instead of making every trail only type `Trail`. This allows queries to find all trails, including more specific trail types, using `rdfs:subClassOf*`.

## Subclass Hierarchy

The subclass hierarchy appears here:

```ttl
:HikingTrail rdfs:subClassOf :Trail .