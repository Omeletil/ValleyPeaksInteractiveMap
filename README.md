# Valley Peaks Location Atlas

Open **index.html** in a browser. All map data and images are local; no server or game modification is needed. Keep the accompanying files in the same folder. To publish the map, upload the folder's contents to a static website host.

The interactive view covers the two main worlds. Select Autumn or Winter, choose categories, search by NPC/quest/object name, then click a marker. Selecting a quest participant also shows linked quest givers, pickups and targets. Drag to pan, scroll to zoom, or use the zoom buttons. Height is the original world Y coordinate, which helps distinguish mountain and ground-level locations.

## What was extracted

- **2,316 selected scene placements** across the two main worlds and two tutorial scenes. These are raw placements, not a completion checklist.
- **43 directly referenced NPC quests**: 22 autumn quest givers and 21 winter quest givers, with names, journal titles, linked quest pickups/targets and positions.
- Currency mushrooms, bolts, polaroids, juice pickups, chests, eggs, shrines, suitcases and clothing-source components, plus other NPCs.
- Initial active status, object/component IDs, hierarchy, container ancestry and selected alternate NPC positions.
- Both actual game map backgrounds: 25 tiles per season, stitched to 2560×2560 pixels.

The interactive map covers Autumn and Winter. The CSV and JSON additionally contain 39 tutorial placements. Main-world counts: Autumn 1,142; Winter 1,135. Per-category counts are in `counts.json`.

## Data and accuracy

`locations.json` retains marker and quest relationships; `locations.csv` provides a flat table. Marker IDs use scene filename and component PathID, rather than runtime-generated save IDs. The same object in autumn and winter has separate records.

Juice display names use consistent spelling and consecutive guide numbers, such as `Apple Juice #1` and `Blueberry Juice #1`. Numbering starts at 1 for each flavour in each season and includes all exported placements. These are guide labels, not game save IDs or a suggested collection order. Original Unity names, including prefab suffixes and typos, remain in `object_name` and the source hierarchy for traceability.

The assemblies describe object types and relationships; the Unity scene assets hold the actual instances and transforms. Parent translation, rotation and scale were composed to calculate world positions. No game code was executed to obtain these records, and the installed game files were not modified.

NPC names come from `NpcBase.FrogName[0]`, falling back to the GameObject name. Quest titles were joined through the initially active QuestLogControl and its indexed QuestPanel references to the TMP text. This matters because the winter scene also contains an inactive copy of the autumn journal with overlapping quest IDs. Descriptions use quest component fields, with the matching journal text as a fallback for empty fields.

All 2,580 selected MonoBehaviour records decoded to their exact serialized byte lengths. Quest-link checks found no unresolved direct quest-giver references or unlinked exported quest pickups. GameObject active flags were validated against the serialized layout. Browser checks covered searching, selecting a quest and its locations, switching seasons, showing all categories and mobile layout.

Positions reflect stored scene data and have not been independently checked during gameplay. The map includes inactive objects, child rewards, variants, and locations that may move or become available later. Transform positions identify scene objects; the physical collider centers matched those positions for three sampled quest pickups. Filtering by initial activity alone would discard quest items and other unlockable content.

Carl's quest references `QI-Bracelet 2` near town at X −337.29, Y 1.652, Z 129.974, while the quest description says Mt. Croob. Its collider agrees with the stored location; a child-model offset does not explain the difference. The map follows the stored quest-item reference. The cause of the discrepancy is unknown.

The dataset covers selected component types in four gameplay scenes. It excludes other scenes, prefab-only spawns and some collectible and minigame reward types. The main radio objective, dynamically created journal quests and other landmarks are not fully represented. Some marker labels use the game's object names. Known moving NPC positions are included where their quest classes expose them; additional animation or scripted movement may exist.

Coverage corresponds to the bundled game build. Game updates can change locations, IDs and quest behavior.

## Projection

Both backgrounds span world X **−1215.25 to 284.75** and Z **−654.5 to 845.5**. Positive X points right and positive Z points up. At 2560×2560 resolution:

```text
pixel_x = (world_x + 1215.25) * 2560 / 1500
pixel_y = (845.5 - world_z) * 2560 / 1500
```

These bounds come from 25 serialized MinimapScanner placements, each covering 300 world units with a 512×512 texture. `map-backgrounds.json` records source textures and bounds. `source-build.json` records Unity version and SHA-256 hashes to identify the source build; a game update may change object IDs and placements.