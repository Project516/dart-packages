# liquid_glass

Apple Liquid Glass as a Flutter platform view: `UIGlassEffect` on iOS 26 and
`NSGlassEffectView` on macOS 26, with a system blur below those releases.

```dart
LiquidGlass(
  cornerRadius: 24,
  child: const Padding(
    padding: EdgeInsets.all(16),
    child: Text('On glass'),
  ),
)
```

Off iOS and macOS, including the web, `LiquidGlass` is just its `child`, so a
caller needs no platform branch. `liquidGlassSupported()` answers whether the
OS draws real Liquid Glass rather than the fallback blur.

## Options

- `cornerRadius`: corner radius in logical pixels.
- `tint`: a color mixed into the glass. Keep it near-transparent.
- `interactive`: the glass reacts to touch. The native view then takes the
  touches, so buttons in `child` stop receiving them.
- `brightness`: forces light or dark glass. Null follows the system. Pass the
  app's resolved brightness when its theme can differ from the system.

With Reduce Transparency on, the glass draws as a solid, opaque surface.

## Groups

`LiquidGlassGroup` puts the `LiquidGlass` surfaces under it in one native
container (`UIGlassContainerEffect` / `NSGlassEffectContainerView`), so they
blend into each other when they come within `spacing`. Glass samples what is
painted below the group, so put the group above the content it should
refract:

```dart
Stack(
  children: <Widget>[
    body,
    LiquidGlassGroup(
      spacing: 40,
      child: Stack(children: <Widget>[appBar, tabBar]),
    ),
  ],
)
```

A member hidden with `Offstage` or `Visibility(visible: false)` keeps its
shape in the container. Build it conditionally instead.

## Things worth knowing before using it

- **It is configured once, at creation.** Rebuilding with a different
  `cornerRadius`, `tint` or `brightness` changes nothing. Pass a `Key` that
  varies with those values so the element is replaced.
- **It is expensive compared to a painted box.** Use it for fixed chrome such
  as a bar, a menu or a floating panel, never per row in a scrolling list.
- `brightness` is not yet honored on a `LiquidGlass` inside a
  `LiquidGlassGroup`.
