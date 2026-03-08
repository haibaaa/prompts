
STRICT ASCII DIAGRAM GENERATION RULES FOR LLMs
==============================================

Purpose
-------
Generate clean, readable ASCII diagrams that render correctly in
terminal environments (glow, bat, less, neovim, mdcat).

Diagrams must resemble those used in real technical documentation
and source code comments.

Maximum width: 90 characters
Maximum height: 25 lines

----------------------------------------------------------------

1. MONOSPACE ASSUMPTION

All diagrams assume a monospaced font.

Every character occupies exactly one column.

If alignment depends on proportional fonts,
the diagram is invalid.

----------------------------------------------------------------

2. ALLOWED CHARACTERS

Use only simple ASCII characters:

Lines:
- | /

Arrows:
> < ^ v

Boxes:
[ ]
( )
+

Branching:
+--

Avoid:
Unicode box characters
emoji
ASCII art shading
decorative symbols

----------------------------------------------------------------

3. DIAGRAMS MUST BE IN CODE BLOCKS

Always place diagrams inside fenced code blocks.

Example:

```

Input
|
v
[Process]
|
v
Output

```

Never mix diagrams with normal text.

----------------------------------------------------------------

4. KEEP STRUCTURE SIMPLE

Each diagram must represent ONE concept only:

- process flow
- hierarchy
- architecture
- state machine
- association
- pipeline

Do not combine multiple diagram types.

----------------------------------------------------------------

5. ALIGNMENT IS CRITICAL

Rules:

- vertical connectors must share the same column
- horizontal connectors must share the same row
- arrowheads must align with their lines

Bad:

```

Input
|
v
[Process]

```

Good:

```

Input
|
v
[Process]

```

----------------------------------------------------------------

6. BOX STYLE

Preferred box format:

```

[Component]

```

For larger blocks:

```

+------------------+
| Processing Node  |
+------------------+

```

Rules:

- keep box widths consistent
- text inside box <= box width
- avoid oversized boxes

----------------------------------------------------------------

7. CONNECTION RULES

Connections must be explicit.

Allowed connectors:

Vertical:
|
v
^

Horizontal:
->

Branches:
+--

Avoid diagonal lines unless absolutely necessary.

----------------------------------------------------------------

8. PIPELINE DIAGRAM

Used for linear algorithms or data pipelines.

Example:

```

Input -> Parse -> Validate -> Transform -> Output

```

Rules:

- keep pipelines <= 80 characters
- avoid wrapping

----------------------------------------------------------------

9. VERTICAL FLOW DIAGRAM

Used for procedural steps.

Example:

```

Input
|
v
[Validate]
|
v
[Compute]
|
v
Output

```

Rules:

- nodes stacked vertically
- connectors centered

----------------------------------------------------------------

10. TREE DIAGRAM

Used for hierarchies or module decomposition.

Example:

```

Root
|
+-- Module A
|     |
|     +-- Submodule A1
|     +-- Submodule A2
|
+-- Module B
|
+-- Submodule B1

```

Rules:

- use `+--` for branch nodes
- maintain vertical `|` continuity
- indentation must be consistent

----------------------------------------------------------------

11. ARCHITECTURE DIAGRAM

Used for system components.

Example:

```

```
    [Client]
        |
        v
    [API Gateway]
      /       \
     v         v
```

[Service A] [Service B]
|
v
[Database]

```

Rules:

- top-down layering
- avoid crossing connections
- components represented as boxes

----------------------------------------------------------------

12. DATA FLOW DIAGRAM

Always label flows.

Example:

```

User
|
| request
v
[Auth Service]
|
| token
v
[Application]
|
| response
v
Client

```

Rule:
Every arrow must represent a named data item.

----------------------------------------------------------------

13. STATE MACHINE DIAGRAM

States are nodes.

Transitions are arrows.

Example:

```

[Idle] -> [Running] -> [Completed]
|
v
[Error]

```

Transitions may include labels:

```

[Idle] --start--> [Running]

```

----------------------------------------------------------------

14. UML ASSOCIATION STYLE

Example:

```

[Student] ---- enrolls in ---- [Course]

```

Multiplicity example:

```

Student 10..300 ----> 1..5 Course

```

Rules:
Keep association lines horizontal.

----------------------------------------------------------------

15. LABEL DESIGN

Labels must be short.

Prefer:

Verb phrases for processes
Nouns for components

Good:

Validate Input
Compute RMS
Display Result

Avoid:

Step1
ModuleX
Thing

----------------------------------------------------------------

16. DIAGRAM SIZE CONTROL

Split diagrams if they exceed limits.

Limits:

width <= 90 characters
height <= 25 lines

Prefer multiple smaller diagrams.

----------------------------------------------------------------

17. SYMMETRY

Good diagrams are visually balanced.

Examples:

Balanced:

```

```
  [Gateway]
   /    \
  v      v
```

[Service] [Service]

```

Avoid asymmetrical layouts.

----------------------------------------------------------------

18. NO VISUAL NOISE

Avoid:

- excessive borders
- repeated characters
- unnecessary labels
- large decorative shapes

Minimalism improves readability.

----------------------------------------------------------------

19. CONSISTENT STYLE

Within one document:

- same box style
- same arrow style
- same indentation

Do not mix styles.

----------------------------------------------------------------

20. TERMINAL COMPATIBILITY CHECK

Diagrams must render correctly in:

less
glow
bat
neovim

There must be:

- no wrapping
- no broken alignment
- no Unicode characters

----------------------------------------------------------------

CORE PRINCIPLE
--------------

ASCII diagrams should look like diagrams
commonly found in high-quality software
documentation and code comments.

If the diagram remains perfectly readable
in plain text inside `less`, it is correct.
