## Scenography Rules (v1)

### Composition Anchors
- Widget block is always anchored to the bottom edge of the panel.
- Bottom spacing equals the side padding of the panel.
- The figure is centered if the text allows it.
- If the text is long, the figure shifts downward and keeps equal spacing
  between the text and the widget block.

### Shape Construction
- Size is driven by overall bounding volume, not by edge length.
- Connect vertices minimally: only canonical edges of the shape, no
  internal or all-to-all connections.
- For non-compact shapes, start with a visual estimate and refine after
  inspection.
