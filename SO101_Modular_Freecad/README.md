# SO101 modular FreeCAD project

Open **SO101_Assembly.FCStd** for the complete robot. Its components are external FreeCAD links to the files in `PrintedParts/` and `Hardware/`.

## Edit one printed part

1. Open its `.FCStd` file from `PrintedParts/` in the same FreeCAD session as the assembly.
2. Activate the Body in that part document. Add sketches and Part Design features to the existing imported base, or build replacement geometry in that same Body.
3. Save the part and return to the assembly. Recompute if necessary. The assembly links to the Body, so new features at its Tip are included.
4. Save the assembly when finished. If the part was edited in a different FreeCAD process, close and reopen the assembly to reload the saved component files.

Keep the component Body at its existing local origin. Positioning within the robot is stored on the assembly link. Keep the referenced Body rather than deleting and recreating it; replacing the Body requires updating the assembly link.

These files retain the imported solids. Splitting them does not recover the original sketch/dimension history.

## Gripper files

- `PrintedParts/MovingJaw.FCStd`: moving finger, attached to Link6.
- `PrintedParts/WristRoll_FixedJaw.FCStd`: fixed finger and its integrated wrist/servo support, attached to Link5.
- `PrintedParts/CustomTerminalLink.FCStd`: empty Body at the J6 shaft frame, already linked to Link6. For a replacement moving jaw, build geometry here and hide the existing MovingJaw link in the assembly.

Use `Joints > J6 > Angle` in the assembly to preview gripper movement. J1–J6 and the saved starting pose are preserved. Joint angles have no enforced collision limits.

## Files and portability

- `SO101_Assembly.FCStd`: assembly structure, component placements, and joint expressions.
- `PrintedParts/`: 11 printed parts plus the empty custom terminal Body, each in its own file.
- `Hardware/`: 50 separate reference components, including servo housing pieces, horns, gears, and electronics.
- `components.json`: component names and relative file paths.

Move or share the **whole SO101_Modular folder**. Do not move or rename individual component files without updating their assembly links.

The original `../SO101_6DOF_Editable.FCStd` remains unchanged. Existing invalid servo rear-cover reference geometry is preserved; it is not part of the printed-part redesign.
