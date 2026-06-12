-by keymandis


# Roblox Studio DEV Collaboration Workflow: Decentralized Development via Packages

This guide outlines the official workflow for builders to contribute maps, assets, and 3D geometry to the project without utilizing **Team Create**. This workflow completely bypasses the real-time Team Create age-verification restrictions and parental permission blocks introduced in the 2026 Roblox safety updates.

By using the **Roblox Package System**, builders work completely independently in isolated local files, while scripters and project integrators pull updates directly into the production environment via the Roblox Cloud.

---

## Workflow Overview

```
[ Builder (Local File) ] 
       │
       ▼ (Build Asset/Map)
[ Convert / Publish to Group Package ]
       │
       ▼ (Roblox Cloud Sync)
[ Main Game (Team Create / Git) ](OWNER*(PR REVIEWER)) ──> Right-Click ──> [ Update Package ]
```

### Why This Workflow?
* **Zero Verification Friction:** Builders do not need to upload government IDs, perform face scans, or ask parent accounts(12-17) for "Trusted Connection" overrides.
* **Isolated Environment:** No risk of a builder accidentally breaking live script environments or causing merge conflicts in Git.
* **Granular Control:** Project lead(OWNER) can review and pull build updates when they are ready, rather than dealing with half-finished assets mid-session.

---

## Part 1: DEV Guide (Creating & Modifying Assets)(mostly for builders/modelers/decorators)

As a dev, you will **never** log into the main production Team Create session. You will do 100% of your work inside a local, solo baseplate.

### Step 1: Create a Local Workspace
1. Open Roblox Studio and open a completely blank **Baseplate** file.
2. Save this file locally to your computer (`File > Save to File As...`) as your personal scratchpad (e.g., `Lobby_Workspace.rbxl`).

### Step 2: Convert Your Build to a Package
Once you have finished a model, map section, or asset asset pack:
1. Group your assets into a single `Model` or `Folder` in the **Explorer** window.
2. Right-click the parent `Model`/`Folder` and select **Convert to Package**.
3. In the configuration window, change the **Owner** dropdown from your username to the **Shared Group**.
4. Give the package a proper name (e.g., `Asset_Lobby_Geometry`) and click **Submit**.

>  **Verification:** If successful, the model's icon in your Explorer will change to a **cardboard box icon** (Package), and a `PackageLink` object will appear inside it.

### Step 3: Publishing Changes
Whenever you edit, add to, or change the geometry inside your package:
1. A **green dot** will appear on the package icon in your Explorer, indicating you have unpublished local changes.
2. Right-click the package and select **Publish Changes to Package**.
3. Your updates are now securely uploaded to the Group cloud and ready for the rest of the team.

---

## Part 2: The Integrator / PR REVIEWER GUIDE (Syncing to Production)(LockTacHolder would do this)

LocktacHolder operating in the main production file (or local Rojo environments) can pull builder updates natively.

### Step 1: Insert the Package Into the Game
1. Open the main production game file.
2. Open the **Toolbox** (`View > Toolbox`).
3. Navigate to the **Inventory tab** (the shield icon).
4. Select **My Packages** from the dropdown menu, and filter by your **Group**.
5. Click your builder's package to insert it into the workspace. Position it wherever it belongs in the world.

### Step 2: Syncing Builder Updates
When a builder announces they have published a new version:
1. A **green circular sync arrow** will automatically appear next to the package in the main game's Explorer window.
2. To update, right-click the package and select **Update Package**.
3. The geometry will instantly replace itself with the builder's newest version, perfectly preserving its position, orientation, and attributes within your main map.

---

## Best Practices & Troubleshooting

### 1. Enable Auto-Update for Static Environments
If LockTacHolder don't want to manually right-click to update packages constantly:
* Inside the main game, expand the package and select the `PackageLink` object.
* In the **Properties** window, toggle **AutoUpdate** to `true`.
* Every time the main production file is opened, it will automatically pull the newest published builder changes.

### 2. Strict Separation of Concerns (Geometry vs. Scripts)
To avoid package conflicts and override loops, adhere to this structural rule:
* **Builders only package physical parts, meshes, textures, and UI layouts.**
* Do **not** include functional scripts inside a builder's package.
* Scripters should handle logic externally (e.g., tags via *CollectionService*, or pointing scripts to the package path from a separate `ServerScriptService` directory manage).

### 3. Resolving Package Conflicts
If someone accidentally edits a package inside the main game while the builder is editing it locally, a **red warning icon** will appear.
* To fix this, right-click the conflicted package in the main game.
* Select **Undo Changes** to discard accidental production modifications and align back with the cloud version, or select **Show Changes** to manually resolve which version wins.
