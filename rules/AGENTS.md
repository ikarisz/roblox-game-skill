# Roblox Game Development Rules for Antigravity

These rules enforce essential development, security, and stability guidelines when developing Roblox games or driving Roblox Studio through MCP in Antigravity.

---

## 1. Security & Authority: Never Trust the Client

- **Server-Authoritative Game Logic**: All critical state changes (currency, XP, health, inventory, purchases, cooldowns) must be computed and verified strictly on the server.
- **RemoteEvent Validation**:
  - Treat every RemoteEvent/RemoteFunction payload as untrusted and potentially malicious.
  - Validate player identity, argument types, value ranges, ownership, and rate-limit triggers.
  - Never allow clients to pass damage amounts, transaction values, or target health directly.
- **Client Presentation Only**: Client scripts (`LocalScript`) are strictly for input handling, UI display, camera manipulation, and immediate visual/audio effects.

---

## 2. DataStore Persistence & Session Locking

- **Prevent Data Loss**: Never use raw `SetAsync()` for player progression data.
- **Session Locking Required**: Always use proven session-locking libraries such as `ProfileService` or `ProfileStore` to avoid race conditions and multi-server overwrite bugs.
- **Pcall Wrappers**: Always wrap `DataStoreService` calls in `pcall()` blocks to handle external API rate limits and temporary outages gracefully.
- **Server Shutdown (`BindToClose`)**: Always register a `:BindToClose()` handler to save all active player sessions when servers shut down.

---

## 3. Roblox Studio MCP Execution Guardrails

- **Thread Yielding (`task.wait()`)**:
  - Code executed via `execute_luau` runs on Studio's main thread.
  - For large operations (bulk instance creation, procedural generation, traversing large trees), split the work into manageable batches (~1,000 items) and yield with `task.wait()` per chunk to avoid freezing Studio or dropping the MCP connection.
- **Hierarchy Staging**:
  - When creating many instances, build each batch in a container outside the DataModel (e.g., in a local Folder), then parent it to the DataModel right before `task.wait()`.
- **Mode Awareness (`get_studio_state`)**:
  - Always verify whether Studio is in Edit mode or Play mode before altering the DataModel.
  - Never execute persistent build edits against the edit DataModel while a playtest is active (changes will be discarded on stop).
- **Undo Safety**:
  - Call `ChangeHistoryService:SetWaypoint()` before executing bulk or potentially destructive operations so the user can easily undo changes in Studio.

---

## 4. Code Architecture & Service Placement

- **ServerScriptService**: Server-only logic, data managers, anti-cheat, service orchestrators.
- **ReplicatedStorage**: Shared modules, RemoteEvents, network definitions, client-accessible configuration tables.
- **StarterPlayerScripts**: Client controllers, input handlers, camera managers.
- **StarterGui**: ScreenGuis and UI presentation controllers.
- **ServerStorage**: Server-only maps, asset templates, weapon models cloned on demand.
- **Workspace**: The live 3D world. Keep it organized in named folders; avoid cluttering with unanchored or unused parts.
