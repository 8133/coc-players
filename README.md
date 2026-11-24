<h1 align="center">coc players</h1>

<h3 align="center">a clash of clans database with 8,090,576 player tags</h3>

<p align="center">
  <img src="https://raw.githubusercontent.com/8133/8133/main/assets/clash-of-clans.PNG" width="26" height="26" alt="clash of clans" />
  <a href="https://github.com/8133/coc-players/releases/tag/v1.0.0"><b>download the dataset</b></a>
</p>

<h3> 🛰️ what's in it </h3>

- player tags, display names, xp, town hall levels and weapon levels
- home village and builder base leagues, current and best trophies, and builder hall levels
- clan info, clan roles, donations, clan capital contributions, and labels
- war stars, war preference, attack wins, and defense wins
- **last update:** october 12, 2026 at 09:00 utc (index sync); each player has its own `last_updated` unix timestamp in seconds

some fields may be missing. league and trophy data are from the snapshot; there is no season-by-season ranking history.

<details>
<summary>📋 see a sample player</summary>

one real record, shortened for readability:

```json
{
  "id": 1006,
  "tag": "#P88UVJ",
  "name": "₮ⱧɆ D̷Ʉ₳ⱠI̷₮Ɏ",
  "townHallLevel": 15,
  "townHallWeaponLevel": 1,
  "expLevel": 160,
  "bestTrophies": 3535,
  "warStars": 1207,
  "builderHallLevel": 9,
  "builderBaseTrophies": 1601,
  "clanCapitalContributions": 1831149,
  "clan": {
    "tag": "#8CV0GPPR",
    "name": "Four and Twenty",
    "clanLevel": 36
  },
  "leagueTier": {
    "id": 105000018,
    "name": "Witch League 18"
  },
  "role": "member",
  "last_updated": 1791716012
}
```

</details>

<h3> 📦 download and read </h3>

the release has 17 independently compressed `.jsonl.zst` files. each contains one utf-8 json object per line, sorted by internal player id. download the parts and checksum file to the same directory:

```sh
gh release download v1.0.0 --repo 8133/coc-players
sha256sum -c SHA256SUMS
zstd -dc players-*.jsonl.zst > players.jsonl
wc -l players.jsonl  # 8090576
```

to inspect just one part without writing the decompressed file, run `zstd -dc players-001.jsonl.zst | head`.
