# Quick Brush Engine — Krita Manual 5.3.0 documentation

- Docs »

- Reference Manual »

- Brushes »

- Brush Engines »

- Quick Brush Engine

-

# Quick Brush Engine¶

A Brush Engine inspired by the common artist’s workflow where a simple big brush, like a marker, is used to fill large areas quickly, the Quick Brush engine is an extremely simple, but quick brush, which can give the best performance of all Brush Engines.

It can only change size, blending mode and spacing, and this allows for making big optimisations that aren’t possible with other brush engines.

-
Blending Modes

-
Spacing

-
Size

## Brush¶

The only parameter specific to this brush.

Diameter

The size. This brush engine can only make round dabs, but it can make them really fast despite size.

Spacing

The spacing between the dabs. This brush engine is particular in that it’s faster with a lower spacing, unlike all other brush engines.

See also

Phabricator Task
