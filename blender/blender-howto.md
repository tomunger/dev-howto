# Blender - HowTo

## Try these things

- [ ] Upper right “cavity option” will make edges appear as lines.
- [ ] Vertex data (circle-triangle) auto-smooth. Will auto smooth edges.
- [ ] Tilda key gives view menu?

## Tools

N - right panel

## Selecting

### Manual

- **Ctl-i** : invert selection
- **h** : hide selection
- **Alt-h** : unhide selection

- **Alt-RMB** : select loop

- **Ctl-np+** : select more
- **Ctl-np-** : select less+
- Ctl-Alt-left-click selects all edges same length and direction

### Cursor

**shift-RMB** : move cursor

*Cursor tool:*

- **Shift-C** : move to origin
- **Shift-S** : opens the cursor moving menu

## Moving, Rotating, and Scaling

- **g** : grab an object
  - **X,Y,Z** : move only along this axis
- **s** - Scale scale proportionally
  - **X,Y,Z** : scale only along this axis
  - alt S - scale evenly
  - shift S - fine calling(?)
- **r** - Rotate an object
  - **X,Y,Z** : rotate only around this axis

- **Ctl-A** : "Apply" will apply the transformation, setting values to zero and making the new position the home position
- **-something-** : "Clear" the transformation, returning to home position.

Clear location, rotation, and scale will move the object back to zero position
Apply location, rotation, and scale will zero those attributes, keeping the object in position.

## Modifiers

Modifier operations are only visible in object mode.  Must apply.

## Mesh Editing

- **E** : Extrude
- **I** : Inset faces

- **M** : Merge - merge faces by distance.  Removes small faces. a menu pops up.

## View

Right-click - “smooth”. Render smoothed.

### Bevel tools vs. Bevel modifier

- control the number of segments
- “Harden normals” option.
- Geometry panel “Miter Outer” to “Arc” makes corners rounder

Bevel modifier should often be last.

## Join and split objects

- Bool Tool - Enable.  Use with shift-B
  - Boolean modifier solver “fast” vs “exact”.  Sometimes “exact” produces artifacts?
  - Boolean”slice” seems to cut an object with a surface.
- “Join” operation - ctl-j.
  - “Bool tool” union operation is better.

## Add-ons

Install Machine Tools add on.
