## Quick Use Guide
The first step is to install the dependencies by opening the terminal, navigating to 
the MazeGenerator directory, and running

`pip install matplotlib == 3.5.1`
`pip install numpy`

Next, you should include attached `maze_manager.py` and `solver.py` under the src directory.

Lastly, include attached `quick_start.py` python example under the examples directory. 
If this file ran without any errors, you should be fine to create your own program. 
Use the format outlined in quick_start, or use another example as a template.

The process for creating and solving a maze follows.

    1. Create a maze manager
    2. Add a maze to the manager
    3. Solve the maze
    4. Optionally visualize the results


An example of using the library with different options is shown below.


```python
from __future__ import absolute_import
from src.maze_manager import MazeManager
from src.maze import Maze


if __name__ == "__main__":

    # The easiest way to use the library is through the Manager class. It acts as the glue between
    # The visualization, solver, and maze classes. Mazes inside the manager have unique ids that we use
    # to specify particular mazes.
    manager = MazeManager()

    # We can add mazes to the manager two different ways.
    # The first way, we specify the maze dimensions. The maze that is created gets returned back to you.
    maze = manager.add_maze(20, 20)

    # We can disable showing any output from the solver by entering quiet mode
    # manager.set_quiet_mode(True)

    # If we want to save the maze & maze solution images along with their animations, we need to let the manager know.
    manager.set_filename("myFileName")

    # To see the unsolved maze, call
    manager.show_maze(maze.id)

    # Once we have a maze in the manager, we can tell the manager to solve it with a particular algorithm.
    manager.solve_maze(maze.id, "QLearning")

    # Finally, you can show an image of the maze with the solution path overlaid. All of these display
    # functions will save the figure if MazeManager::set_filename has been set.
    manager.show_solution(maze.id)

```