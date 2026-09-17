# Valley Peaks Location Atlas

Open **index.html** in a browser. All map data and images are local; no server or game modification is needed. Keep the accompanying files in the same folder. To publish the map, upload the folder's contents to a static website host.

The interactive view covers the two main worlds. Select Autumn or Winter, choose categories, search by NPC/quest/object name, then click a marker. Selecting a quest participant also shows linked quest givers, pickups, targets and repair sites. Drag to pan, scroll to zoom, or use the zoom buttons. Height is the original world Y coordinate, which helps distinguish mountain and ground-level locations.

## Completion tracking

Quest givers, polaroids, juices, repairables, stamp-card shops, gacha machines and minigames have completion checkboxes in their marker details. Marking a quest giver records that quest as completed. The sidebar shows progress for the selected season; **Hide completed** removes completed markers from these seven categories. Completion marks are manual; completing a quest does not automatically mark linked pickups.

Progress is saved in this browser for this website. It persists on reload, but does not sync between devices, browsers or website addresses. Clearing site data removes the marks. It is not included in the downloadable map data or hosting ZIP. If browser storage is unavailable, the page reports that changes cannot be saved.

## Repairables

Select **Repairs** to show repairable objects, then use **Repair type** to choose upgrades, a particular upgrade type, shortcuts, or other repairs. Each marker lists its bolt cost, effect and spanner requirement, and can be marked as repaired.

All seven spanner repair quests link to their repair sites. Selecting a quest giver highlights the associated repair even when the Repairables category is unchecked or a different repair type is selected. **Repair:** links in the quest details open the repair marker; selecting the repair also highlights its quest giver. For example, **Repair Keira's Jar!** links to **Jar repair #1**. Quest completion and repair completion remain separate checkboxes; Hide completed still hides completed markers.

The map contains **105 distinct repair locations**: 48 permanent upgrades, 41 shortcuts and 16 other repairs. There are 96 locations in Autumn and 92 in Winter; 83 are shared between the two maps and use the same completion mark in both. Shared repairs include objects from the game's additively loaded StaticScene and the lookout ladder that has matching seasonal copies.

| Upgrade | Autumn | Winter | Effect |
| --- | ---: | ---: | --- |
| Fuel capacity | 15 | 16 | Maximum gadget fuel +7 per repair |
| Fuel regeneration | 18 | 18 | Normal fuel regeneration +2 per second per repair |
| Frost resistance | 10 | 10 | Reduced gadget fuel consumption at high altitude |

These are 19 distinct capacity upgrades, 18 regeneration upgrades and 11 frost-resistance upgrades across both worlds. Frost resistance adds 0.2 to the parameter used in altitude-dependent fuel calculations; it is not a universal 20% reduction. Regeneration remains subject to the game's recharge conditions.

Other repairables include ziplines, jump pads, launcher minecarts, speed rings, ladders, a bridge, season portals, gacha machines, tractors and quest props. Speed rings boost movement and jumping for 5 seconds. The Autumn tractors expose mushroom collectibles as well as an interactive animation; the Winter tractor is associated with a quest. Gacha-machine repairs cost bolts, while later rolls use mushrooms.

Repairs are identified through their actual repaired-branch components and geometry. The 190 stored repair components were audited across the seasonal and shared scenes: 106 active, in-world source placements map to 105 distinct locations after merging the duplicate lookout ladder. Inactive scene copies and unverified inactive objects are excluded, as are nine opposite-season objects parked below the world. Their presence in an asset file does not by itself establish a visitable repair site.

Numbers in names are guide identifiers, not game save IDs or a purchase order. Shared locations are numbered first and keep the same numbers in both worlds; each world's additional repairs follow. Existing completion marks are preserved through stable marker IDs.

## Stamp-card shops and gacha machines

Select **Stamp cards** for the **16 stamp-card shops**, eight in each season. Each sells one completed stamp card, which can be redeemed at a stamp vendor for the next upgrade in that vendor's progression. Prices are 15 mushrooms, except **Winter shop #8**, which costs 12. Mark **Card purchased** after buying it. Autumn and Winter purchases are tracked separately; the shop achievement requires all 16 purchases.

Select **Gacha machines** for the **eight machines shared between both maps**. Each needs a **3-bolt repair**, followed by up to three rolls costing **3, 6 and 9 mushrooms** (18 total). Rolls award random, still-locked cosmetics from a common pool. **Machine finished** means its rolls are complete; **Repaired** is a separate checkbox. Links between the machine and its repair make both states accessible. Each machine and its repair use matching guide numbers and share their completion marks across seasons.

The all-gacha achievement requires **36 cosmetics: 24 from machines and 12 from quests**. Finishing the machines alone does not cover the quest rewards. Use **Show cosmetic quests** in a machine's details, or search quest givers for **gacha reward**, to find the seven Autumn and five Winter quests that award these cosmetics. Their existing quest checkboxes track completion. Machines can also stop early if the common cosmetic pool has already been fully collected.

Shop locations use the physical card displays referenced by their shop controllers. Old shop descriptions naming specific gadgets are not used because the purchase code grants a card. The unused empty shop in each season and the inactive ninth machine are excluded. Machines under initially inactive repaired branches are included when their repair site is active.

## Minigames

Select **Minigames** to show **eight verified entry points**, four per season, covering six achievement types. Markers sit at the NPC who starts the activity. They include the host's name, instructions and the achievement requirement.

| Minigame | Season | Host | Achievement requirement |
| --- | --- | --- | --- |
| Bouldering | Autumn | Pete | Finish the third course; round time limits are 33, 30 and 26 seconds |
| Pumpkin hunt | Both | Toothless | Win the third round; collect 5, then 8, then 10 pumpkins within 50 seconds per round |
| River race | Autumn | Mortimer | Finish the third race in under 22 seconds without failing the course |
| Speed climb | Both | Basher | Finish rounds in under 12, 10 and 8 seconds |
| Memory game | Winter | Basher | Win three rounds with sequences of 3, 5 and 7 rocks |
| Tractor race | Winter | Cooper | Win three races |

**Achievement earned** tracks the achievement. The hunt and speed climb each have entrances in both seasons, and their checkboxes share one achievement mark across those entrances. The game keeps separate seasonal challenge progress for those activities, but completing the qualifying challenge in either season awards the same achievement. Sidebar minigame progress counts distinct achievements available in the selected season.

These locations reuse eight existing NPC records, preserving their IDs, names and positions and moving them from Other NPCs to Minigames. The source controllers directly reference these hosts. Shooting and Whack-a-Goose also appear in the code, but only inactive scene instances were found and their availability was not established; they are outside the mapped minigame coverage.

## What was extracted

- **2,426 exported markers** from the seasonal worlds, tutorial scenes and shared world scene. Counts include dormant objects, variants and rewards inside containers; repairs and gacha rolls have separate markers and completion states. Juice markers include only the 40 active collectible bottles.
- **43 directly referenced NPC quests**: 22 autumn quest givers and 21 winter quest givers, with names, journal titles, linked quest pickups/targets and positions.
- Currency mushrooms, bolts, polaroids, juice pickups, chests, eggs, jars, suitcases and clothing-source components, plus other NPCs.
- **20 juices per season**, with five bottles of each season's four flavours.
- **105 repairable locations**: 96 visible in Autumn and 92 in Winter, including 83 shared locations. These include 48 permanent upgrades plus shortcuts, machines and quest/decorative repairs.
- **16 stamp-card shops**, **eight shared gacha machines** and cosmetic-reward details on **12 existing quest givers**.
- **Eight minigame entry points**, covering six achievement types, identified through their controller-to-host references.
- Initial active status, object/component IDs, hierarchy, container ancestry and selected alternate NPC positions.
- Both actual game map backgrounds: 25 tiles per season, stitched to 2560×2560 pixels.

The interactive map covers Autumn and Winter. The CSV and JSON additionally contain 39 tutorial placements. Main-world marker counts: Autumn 1,249; Winter 1,229. These counts each include 91 shared markers (83 repairs and eight gacha machines), which are stored only once in JSON and CSV. Per-category counts are in `counts.json`.

## Data and accuracy

`locations.json` retains marker and quest relationships; `locations.csv` provides a flat table. Marker IDs use scene filename and component PathID, rather than runtime-generated save IDs. Season-specific objects have separate records. Shared repairs and machines use `scene: Shared` and `worlds: [Autumn, Winter]`; repairs' `repair_source_ids` retain the source instances. Shops retain their controller reference in `shop_source_id`; machines and repairs are linked through `repair_id` and `gacha_id`. Quest givers' `gacha_reward_index` identifies the cosmetic rewarded by their linked quest.

The map calls the `InteractableShrine` category **Jars**, matching the player-facing terminology. Original object/component names remain in the source details.

Juices include 20 collectible bottles per season: Autumn has five each of Apple, Grapefruit, Blueberry and Cherry; Winter has five each of Kiwi, Lime, Pomegranate and Watermelon. Both the bottle component and its object hierarchy must be active. Inactive opposite-season bottles and old shop displays are excluded; all retained bottles also reference active item objects. Each flavour is numbered #1–#5. These are guide labels, not game save IDs or a suggested collection order. Original Unity names, including prefab suffixes and typos, remain in `object_name` and the source hierarchy for traceability. Completion marks use stable marker IDs, so renumbering a bottle does not reset its mark.

Quest repair links follow the repaired construct's enabled `BuildingQuestObject.OnBuilt` event to the exact quest's `CollectItem` method, corroborated by the quest's broken-construct reference. They are stored as quest `repair_ids` and reciprocal marker links with role `repair`. No location-proximity matching is used. Tobin's wind turbine is a lever-code puzzle, rather than one of these spanner repair quests.

The assemblies describe object types and relationships; the Unity scene assets hold the actual instances and transforms. Parent translation, rotation and scale were composed to calculate world positions. No game code was executed to obtain these records, and the installed game files were not modified.

NPC names come from `NpcBase.FrogName[0]`, falling back to the GameObject name. Quest titles and descriptions come from the initially active QuestLogControl and its indexed QuestPanel references to the journal TMP text. This matters because the winter scene also contains an inactive copy of the autumn journal with overlapping quest IDs. Unused descriptions stored on quest components are excluded because many contain copied text from unrelated quests. Display text removes journal formatting and corrects confirmed name typos; original journal strings remain in each quest's `journal_text` record, with changes listed in `text_corrections`. Gerard, Mikey and Ed use the names of their linked quest givers. Return instructions are omitted when their journal textbox is hidden, including unused delivery-quest text.

All 2,580 original selected MonoBehaviour records, 222 additional repair-system records, 113 shop/gacha records and 51 minigame controller/helper records decoded to their exact serialized byte lengths. The minigame extraction also validated 15 linked components. Repair effects were checked against gameplay components under the repaired constructs; bridge and ladder roles also use their authored geometry and names. Shop prices come from the purchase component, and gacha costs, quest rewards and minigame achievement conditions were checked against the gameplay code. Quest-link checks found no unresolved direct quest-giver references or unlinked exported quest pickups. GameObject active flags were validated against the serialized layout. Browser checks cover searching, selecting linked locations, switching seasons, completion persistence, shared progress, filtering and mobile layout.

Positions reflect stored scene data and have not been independently checked during gameplay. The map includes inactive objects, child rewards, variants, and locations that may move or become available later. Transform positions identify scene objects; the physical collider centers matched those positions for three sampled quest pickups. Filtering by initial activity alone would discard quest items and other unlockable content.

The dataset covers selected component types in four seasonal/tutorial scenes, plus repairs and gacha machines from the shared scene loaded by both main worlds. It excludes other scenes, prefab-only spawns and some collectible and minigame reward types. The main radio objective, dynamically created journal quests and other landmarks are not fully represented. Some marker labels use the game's object names. Known moving NPC positions are included where their quest classes expose them; additional animation or scripted movement may exist.

Coverage corresponds to the bundled game build. Game updates can change locations, IDs and quest behavior.

## Projection

Both backgrounds span world X **−1215.25 to 284.75** and Z **−654.5 to 845.5**. Positive X points right and positive Z points up. At 2560×2560 resolution:

```text
pixel_x = (world_x + 1215.25) * 2560 / 1500
pixel_y = (845.5 - world_z) * 2560 / 1500
```

These bounds come from 25 serialized MinimapScanner placements, each covering 300 world units with a 512×512 texture. `map-backgrounds.json` records source textures and bounds. `source-build.json` records Unity version and SHA-256 hashes to identify the source build; a game update may change object IDs and placements.
