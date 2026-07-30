# Class Diagram - Reactor Matrix Architecture

This diagram details the object-oriented structure of the simulation framework, highlighting structural inheritance and class associations.

```mermaid
classDiagram
    class Substance {
        +str name
        +MatrixNode current_node
    }

    class Engineer {
        +int plasma_charges
        +bool is_functional
        +traverse(MatrixNode target_node)
    }

    class MatrixNode {
        +int node_id
        +list adjacent_nodes
        +str anomaly
    }

    class ReactorCore {
        +dict matrix
        +Engineer player
        +MatrixNode singularity_node
        +generate_matrix_grid()
        +deploy_entities()
        +scan_environment()
        +handle_environmental_hazard()
        +execute_system_loop()
    }

    Substance <|-- Engineer : Inherits via Super Constructor
    ReactorCore "1" *-- "20" MatrixNode : Composition (Generates Grid)
    ReactorCore "1" --o "1" Engineer : Directs Actions
