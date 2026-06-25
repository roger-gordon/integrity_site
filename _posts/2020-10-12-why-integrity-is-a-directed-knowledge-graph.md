---
layout: post
title: "Why Integrity is a Directed Knowledge Graph"
date: 2020-10-12
description: Integrity is working to link up disparate data sources, record the provenance of that data, and find the relationships contained within.
image: assets/images/blog-2020-funder-network-app.jpg
author: Roger Gordon
tags: [integrity, graph database, open access]
nav-menu: false
show_tile: false
---

The response to Integrity has been incredibly encouraging in the few weeks since we announced it to the scholarly and academic world. Many of the questions posed to us will be addressed in future blog posts, if not sooner.

I'd like to update you on the progress of Integrity, a directed knowledge graph of scholarly and scientific publishing information that uses reputable sources of open access metadata.

Integrity is working to link up disparate data sources; record the provenance of that data; and find the relationships contained within — for instance, among **Institutes**, **Funders**, **Contributors** and **Articles**.

A "directed" graph means that a relationship between two data points flows in a specific direction; this directionality provides structure to the graph and can assist in finding centrality because the beginning and target nodes are defined. In other words, relationships between data can be symmetric or asymmetric, and an asymmetric or directed relationship should be encoded as clearly as possible — the structure of the graph expresses the meaning.

![Integrity knowledge graph — October 2020]({{ "assets/images/blog-2020-knowledge-graph-detail.png" | relative_url }})

As Amy Holder of Neo4j writes:

*"At a high level, knowledge graphs are interlinked sets of facts that describe real-world entities, facts or things and their interrelations in a human understandable form. Unlike a simple knowledge base with flat structures and static content, a knowledge graph acquires and integrates adjacent information using data relationships to derive new knowledge."*

At the moment we're melding DOAJ, ORCID and Crossref records. Some of the DOAJ and ORCID data are without DOIs, so we are using Crossref, custom Python code and Neo4j Cypher to find credible and distinct matches that fill in the missing data.

The next step is to run AI over the keywords and the contributors to disambiguate — systematically and at scale.
