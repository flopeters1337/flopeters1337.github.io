---
title: "Surviving State Tree: A Real Case Study With Dinosaurs"
category: talks
date: 2024-01-01
header:
    teaser: assets/images/st-teaser.png
    overlay_image: assets/images/st-teaser.png
    overlay_filter: 0.3
    caption: "Photo credit: **Epic Games** on [**dev.epicgames.com**](https://dev.epicgames.com/documentation/unreal-engine/state-tree-in-unreal-engine)"
    show_overlay_excerpt: false
tags: talk ai state-trees unreal-engine programming decision-making
---

{% include video id="zovPQnq7ndE" provider="youtube" %}

In 2024, I investigated a (then) new AI feature in Unreal Engine called 'State Tree'. It was still experimental back then. Most of the documentation did not exist or was of poor quality.
The new state trees turned out to be just the right tool for the game [Goner](https://store.steampowered.com/app/1420200/GONER/) that I was assigned to.
The game required complex interactions between autonomous game agents, but still needed to be comprehensive enough that game designers could tweak these interactions easily.
With the guidance of my friend and colleague, Corentin Lemasson, we came up with our own custom traditional AI pipeline to fulfill those needs.
As part of Unreal Fest Seattle 2024, we presented that pipeline in great detail.
