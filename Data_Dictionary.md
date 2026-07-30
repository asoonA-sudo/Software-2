# Data Dictionary  Void Core

This document outlines the data types, structures, and properties used within the Quantum Reactor Matrix simulation engine.
## Classes and Subprograms

### 1. MatrixNode
| Data Component | Type | Description |
| :--- | :--- | :--- |
| `node_id` | Integer | Unique identifier for the specific grid sector (1 to 20). |
| `adjacent_nodes`| List (Integers)| Collection of connected gateway path IDs accessible from this node. |
| `anomaly` | String / None | Current structural hazard state: `"singularity"`, `"radiation_leak"`, `"plasma_vent"`, or `None`. |

### 2. Substance (Base Parent Class)
| Data Component | Type | Description |
| :--- | :--- | :--- |
| `name` | String | The designation of the manifesting physical entity. |
| `current_node` | MatrixNode | Pointer reference to the exact sector object where the substance resides. |

### 3. Engineer (Inherits from Substance)
| Data Component | Type | Description |
| :--- | :--- | :--- |
| `plasma_charges`| Integer | Remaining Ionized Plasma Overloader shots (Starts at 3). |
| `is_functional` | Boolean | Life metric tracking operational capability (`True`/`False`). |
| `traverse()` | Method | Shifts the player reference to a validated adjacent `MatrixNode`. |

### 4. ReactorCore (Game Engine)
| Data Component | Type | Description |
| :--- | :--- | :--- |
| `matrix` | Dictionary | Hash map holding the core topology: `{ int_id: MatrixNode_Object }`. |
| `player` | Engineer | Reference pointer tracking the active player instance. |
| `singularity_node`| MatrixNode | Tracks the target destination sector hosting the primary anomaly. |
| `scan_environment()`| Method | Iterates through adjacent sectors to output warning telemetry text. |
| `handle_environmental_hazard()`| Method | Resolves penalty systems or execution states based on hazard collisions. |
