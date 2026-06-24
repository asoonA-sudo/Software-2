# Data Dictionary  Void Core

This document outlines the data types, structures, and properties used within the Quantum Reactor Matrix simulation engine.
## Classes and Subprograms

### 1. MatrixNode
| Data Component | Type | Description |
| :--- | :--- | :--- |
| 'node_id` | Integer | Unique identifier for the specific grid sector (1 to 20). |
| 'adjacent_nodes`| List (Integers)| Collection of connected gateway path IDs accessible from this node. |
| 'anomaly` | String / None | Current structural hazard state: '"singularity"', '"radiation_leak', '"plasma_vent"', or 'None`. |
