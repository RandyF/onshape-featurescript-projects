# Sub-Project Triage Questionaire

The following sub-project documentatation needs to be started using the Lightweight Development Process.

Create L1 documenation for the following sub-projects

## LOGO Turtle Engine

- Implements the vintage LOGO scripting language to create unique procedural objects in OnShape.
- Implements the 'Turtle' object that will process and execute commands fed by the LOGO engine.
- Turtle maintains position and orientation in the 3D OnShape workspace.
- The intial target is to implement the FORWARD, RIGHT, and LEFT commands.
- The turtle can freely process commands and move within the OnShape workspace.
- The turtle records a path of line segments that concatonate with each FORWARD command.
- The composite 3d path is the primary output for the turtle engine, which that can then be used for further onshape modeling.
- The turtle may be provided a starting point, but shall default to the origin.

## Flat Surface Drawing

- Uses the LOGO Turtle Engine navigate the Turtle and create a path given a 2-dimensional shape.
- The turtle shall have an optional starting point, but if none is provided, the geometric center of the object (within reasonable accuracy) shall be used.
- This drawing mode provides a limitation layer over the standard logo turtle engine where the turtle must stay within the shape provided.
- Standard commands are allowed but FORWARD shall be limited by the boundary of the shape - the turtle shall stop a the edge if encountered.

## Path Following Modes

### Basic Path Following

- Uses the LOGO Turtle Engine to navigate using a provided path as a reference.
- The starting point in this mode is the start of the provided path.
- The basic operation in this mode is to movve the turtle in relation to the path provided with different possible movements around that path.
- Primary operation of the folower mode is to maintain a path position and tangent vector.
- The FORWARD operation moves the PATH REFERENCE that far along the provided path.
- Basic Path Following blocks the RIGHT and LEFT commands, as they are undefined in this mode.
- As a basic mode, the turtle follows the provided path returning a segmented path defined by the FORWARD commands.

### Disk Path Following

- Uses the Basic Path Following to move the turtle along a path.
- A Disk Radius parameter or a guide path must be provided as a parameter.
- The turtle starting point is 1-disk-radius from the path, or a the start of the guide path.
- When a RIGHT or LEFT command is provided, the path reference disk rotates around the current path tanget, the turtle does not move.
- A FORWARD command does the following:
    - moves the path reference forward maintaining the current rotation
    - if a guide path is provided, determine the new disk radius by finding the distance between the primary path and the guide path by percentage traveled.
    - Find the point one-radius from the primary path with respect to the path tangent and current orientation.    
    - Move the turtle to the edge of the disk created by the new path reference position creating a single path segment between the previous position and the next position.


# Architecture Component Hints

- OnShape Workspace
- OnShape FeatureScript Engine
- LOGO Turtle Engine
- 2D Constraint Module
- Path Following Core Module
- Disk Path Following Module