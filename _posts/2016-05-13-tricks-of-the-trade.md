---
dateModified: '2016-05-13T12:39:48.383Z'
hasPage: false
inFeed: true
inNav: false
title: Tricks of the Trade
description: 'One of my side projects right now is to use figure out how to do agent-based simulation modeling (ABM) with in-memory data grids (like Hazelcast). A typical ABM assigns a behavior or reflex to agents based on their read of the environment. This usually happens by putting all of the code objects that represent agents into a list and iterating through the list to call on each object/agent to do some observation action, like counting neighbors or detecting a system state.'
author: []
starred: false
datePublished: '2016-05-13T12:40:56.748Z'
sourcePath: _posts/2016-05-13-tricks-of-the-trade.md
_context: 'http://schema.org'
_type: Article

---
# Tricks of the Trade

One of my side projects right now is to use figure out how to do agent-based simulation modeling (ABM) with in-memory data grids (like [Hazelcast][0]). A typical ABM assigns a behavior or reflex to agents based on their read of the environment. This usually happens by putting all of the code objects that represent agents into a list and iterating through the list to call on each object/agent to do some observation action, like counting neighbors or detecting a system state.

Hazelcast uses a Java 'map' to contain the objects/agents. And while the map is iterable (meaning you can start with one item in the map and turn to the next, then the next, then the next and so on... it does not easily 'subitize'. You cannot easily pick just a few items in the map and iterate through those.

Today, I read a nice article from DZone on iterating with maps. This is getting easier with Java 8 and the solution was impressively simple. I haven't tried it yet, but I wanted to share it. [Take a look][1]!

[0]: http://hazelcast.org/ "Hazelcast"
[1]: https://dzone.com/articles/iterating-java-map-entries?utm_source=Top%205&utm_medium=email&utm_campaign=top5%202016-05-13 "Iterating on Java Maps"