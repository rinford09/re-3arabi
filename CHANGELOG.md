# Changelog

All notable changes to the `re-3arabi` CloudStream plugins repository will be documented in this file.
The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [1.0.0] - 2026-10-28

### Milestone: AnimeWitcher Multi-Facet Filters & ADM Batch Download Fix
* **Git Tag**: `v1.0.0`
* **Plugin Version**: `Animewitcher v4`
* **Repository**: [github.com/rinford09/re-3arabi](https://github.com/rinford09/re-3arabi)

### Added
- **AnimeWitcher Advanced Algolia Multi-Facet Tokenizer**:
  - Implemented regular expression token parser for structured search queries:
    - `tag:<value>` or `genre:<value>` -> Maps to Algolia genre taxonomy.
    - `studio:<value>` -> Filters by animation studio (MAPPA, Toei Animation, Madhouse, etc.).
    - `year:<value>` -> Filters by release year (e.g. `2024`, `1999`).
    - `state:<value>` -> Filters by ongoing (`مستمر`) or completed (`مكتمل`) status.
    - `type:<value>` -> Filters by anime format (`مسلسل`, `فيلم`, `أونا`, `أوفا`, `حلقة خاصة`).
    - `season:<value>` -> Filters by season (`خريف`, `شتاء`, `ربيع`, `صيف`).
    - `age:<value>` -> Filters by audience age rating (`+13`, `+17`, `+18`, etc.).
  - **Grouped Disjunctions (OR)**: Multiple chips within the same category (e.g. multiple genres or multiple studios) are joined with OR logic in Algolia `facetFilters`.
  - **Conjunctions (AND)**: Separate categories are intersected with AND logic.
  - **Year-Season Cross Expansion**: Allows combination queries such as `year:2024 season:خريف`.
  - **Freeform Query Preservation**: Free-text titles can be seamlessly mixed with filter tags (e.g. `One Piece state:مستمر`).

### Fixed
- **ADM Episode Batch Download**:
  - Fixed client error occurring when batch-downloading episodes via ADM (Advanced Download Manager).
  - Ensured reliable direct video link resolution and stream URL extraction for external download handlers.

### Changed
- **Version Bump**: Bumped `Animewitcher` plugin version from `3` to `4` in `Animewitcher/build.gradle.kts`.
- **Repository Index**: Updated `repo.json` to point to `rinford09/re-3arabi`.

---

### How to Roll Back to this Version:
To restore or inspect the repository exactly at this milestone:
```bash
git checkout v1.0.0
```
To return to the latest development branch:
```bash
git checkout main
```
