import unittest

# Import classes from your main script
# from main import MatrixNode, Substance, Engineer


class TestEngineerClass(unittest.TestCase):

    def setUp(self):
        """Set up fresh node objects and engineer instance before every test."""
        self.node_alpha = MatrixNode("Sector 1 - Command Bridge")
        self.node_beta = MatrixNode("Sector 2 - Engineering")
        self.node_gamma = MatrixNode("Sector 3 - Reactor")

        self.engineer = Engineer(
            name="Isaac Clarke", starting_node=self.node_alpha
        )

    def test_initialization_and_inheritance(self):
        """Verify that inheritance from Substance sets properties correctly."""
        self.assertEqual(self.engineer.name, "Isaac Clarke")
        self.assertEqual(self.engineer.current_node, self.node_alpha)
        self.assertEqual(self.engineer.plasma_charges, 3)
        self.assertTrue(self.engineer.is_functional)

    def test_valid_traversal(self):
        """Verify that traverse updates the current_node attribute."""
        self.engineer.traverse(self.node_beta)
        self.assertEqual(
            self.engineer.current_node,
            self.node_beta,
            "Engineer should be in Sector 2",
        )

        # Multi-step traversal
        self.engineer.traverse(self.node_gamma)
        self.assertEqual(
            self.engineer.current_node,
            self.node_gamma,
            "Engineer should be in Sector 3",
        )

    def test_traversal_when_non_functional(self):
        """Verify that non-functional engineers cannot move."""
        self.engineer.is_functional = False
        self.engineer.traverse(self.node_beta)

        # Node should NOT have changed
        self.assertEqual(
            self.engineer.current_node,
            self.node_alpha,
            "Non-functional engineer should remain at original node",
        )


if __name__ == "__main__":
    unittest.main()
