# Neo4j Customer Purchase Network

This project is a graph database assignment for the Big Data 2 (ITE 5424) course. It models customers, food items, and their relationships using Neo4j and Cypher. The primary focus is on analyzing customer purchase patterns and product relationships using graph-based queries.

- **Name:** Gurjit Singh  
- **Student ID:** N01634963  
- **Course:** Big Data 2 (ITE 5424)

## Overview

This project involves:

- Creating nodes for `Customer`, `Item`, and `Group`
- Creating relationships such as `BUYS` (between customers and items) and `IN_GROUP` (between items and item groups)
- Running complex Cypher queries to analyze:
  - Product recommendations
  - Most frequently bought items
  - Co-purchased items
  - Product group trends
  - Student-project modeling with various query patterns

## Technologies Used

- Neo4j
- Cypher Query Language

## Project Structure

- Node creation: Customers, Items, Groups
- Relationship creation:
  - `(:Customer)-[:BUYS]->(:Item)`
  - `(:Item)-[:IN_GROUP]->(:Group)`
- Analytical queries:
  - Recommendations based on co-purchases
  - Item popularity
  - Group-based purchase statistics
- Student-Project Graph: Includes queries based on working hours and project allocations

## Setup Instructions

1. Install Neo4j Desktop or use Neo4j Aura
2. Create a new database
3. Copy and run the Cypher script in `assignment.cypher`
4. Run analytical queries included in the same script

## Sample Queries

- Recommend items to a customer based on similar users:
  ```cypher
  MATCH (c:Customer{Name:"Orren"})-[:BUYS]->(i:Item)<-[:BUYS]-(oc:Customer)-[:BUYS]->(oi:Item)
  RETURN oi.Name AS RecommendedItem, count(oc) AS Score
  ORDER BY Score DESC;
