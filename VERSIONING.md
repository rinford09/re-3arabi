# Plugin Versioning & Release Protocol

This repository adheres to [Semantic Versioning (SemVer)](https://semver.org/) for the repository tags and sequential integer versioning for individual CloudStream plugins.

---

## 🏷️ Version Stamp Rules

1. **Individual Plugin Versions (`<PluginName>/build.gradle.kts`)**:
   - CloudStream plugin system tracks each plugin via an integer: `version = <number>`.
   - Whenever any plugin is edited, increment its `version` integer (e.g. `version = 4` -> `version = 5`).
   - CloudStream detects this integer to notify users of plugin updates.

2. **Repository Milestone Tags**:
   - Repository releases follow standard SemVer: `v<MAJOR>.<MINOR>.<PATCH>` (e.g., `v1.0.0`, `v1.1.0`).

---

## 📋 Steps for Any Future Update

Whenever making changes to any plugin:

1. **Increment Plugin Version**:
   In the modified plugin's `build.gradle.kts` (e.g. `Animewitcher/build.gradle.kts`):
   ```kotlin
   version = 5 // increment by 1
   ```

2. **Update `CHANGELOG.md`**:
   Document changes under a new version heading:
   ```markdown
   ## [1.1.0] - YYYY-MM-DD
   ### Milestone: <Title of Update>
   * **Git Tag**: `v1.1.0`
   * **Plugin Version**: `<PluginName> v5`
   
   ### Added / Fixed / Changed
   - Details of what changed...
   ```

3. **Commit and Tag**:
   ```powershell
   git add .
   git commit -m "feat(<plugin>): description of update (v1.1.0)"
   git tag -a v1.1.0 -m "Release v1.1.0: description of update"
   ```

4. **Push to GitHub**:
   ```powershell
   git push origin main --tags
   ```
   GitHub Actions will automatically build the new `.cs3` files and update the `builds` branch index.

---

## ⏪ Rollback Instructions

To roll back or inspect any historical version:

* **View all tags**:
  ```powershell
  git tag -n
  ```

* **Roll back / inspect any version**:
  ```powershell
  git checkout v1.0.0
  ```

* **Return to latest code**:
  ```powershell
  git checkout main
  ```
