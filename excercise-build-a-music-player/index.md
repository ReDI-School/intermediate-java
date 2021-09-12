---
title: Exercise - Building music player
nav_order: 0
has_children: true
nav_exclude: true
---

# Lesson 21: Exercise - Building music player

## Goals

- Learn how we can use the data structures we've learned about in order to solve real problems
- Use object oriented paradigms together with complex data structures
- Get more confident transforming requirements into code
- Train on exercise to make own project

## Task

Today will be all about music. We're going to build a streaming service.

The feature our users want most, is to gather listening statistics per track, per artist and per user.

## Requirements:

Our base entity is the track. It has an id, a name, an artist.

Our streaming service should have one player, that, once it is invoked with a track,
will print `"Now playing: <artist_name> - <track_name>"`.

Our users are interested in:

- Who was their top artist?
- Which was their favorite track?

Our artists are interested in:

- Who is my top fan? (Most played tracks)
- How many different users have streamed my music?

Our business-model is simple and we have to pay by the number of streams that happened. Therefore our business wants
to know:

- How many streams have there been in total?
