Project: Space Station Matrix Game (Engineer Class System)
Entry 1: Architecture & Inherited State Design
Goal: Establish a modular object-oriented foundation where physical entities in the environment (Substance) are decoupled from specific player mechanics (Engineer), while both interface seamlessly with space locations (MatrixNode).

Implementation:

Defined MatrixNode to represent discrete room locations/sectors across the station matrix.

Defined Substance as the base physical entity class carrying foundational spatial attributes: name and starting_node (which maps to current_node).

Derived Engineer from Substance to encapsulate specialised player properties (plasma_charges, is_functional).

Problem Encountered:

Initial subclass implementations omitted the explicit call to super().__init__(), resulting in AttributeError: 'Engineer' object has no attribute 'current_node' whenever traversal methods were invoked.

Resolution:

Explicitly invoked super().__init__(name, starting_node) within Engineer.__init__() to properly pass spatial initialisation to the parent Substance class.

Entry 2: Traversal Logic & Lifecycle Control
Goal: Implement non-grid traversal methods allowing player-controlled entities to shift positions across MatrixNode instances.

Implementation:

Created Engineer.traverse(target_node) to accept a MatrixNode reference and update self.current_node.

Added conditional state checks (self.is_functional) to govern whether movement actions are permitted.

Problem Encountered:

Direct attribute assignment to current_node outside class methods allowed state updates even when the player was marked as non-functional (is_functional = False).

Resolution:

Enforced encapsulation by ensuring node updates occur strictly through traverse(), checking self.is_functional prior to updating state references.

