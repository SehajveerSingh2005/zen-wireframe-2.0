
# Wireframe Theme Configuration

## Preferences Implementation

This theme implements customizable preferences using Zen Browser's preference system. Preferences are defined in `preferences.json` and can be accessed through Zen Browser's preferences interface.

## Available Preferences

### Boolean Preferences

1. `zen.view.use-single-toolbar` - Use single toolbar layout
2. `wireframe.animations.enabled` - Enable animations in Wireframe theme
3. `wireframe.borders.squared` - Use squared borders
4. `wireframe.urlbar.position.top` - Position URL bar at the top (for multiple and collapsed toolbar only)
5. `wireframe.macos.controls` - Disable macOS style window controls
6. `zen.view.experimental-force-window-controls-left` - Force window controls to the left (for macOS style controls only)
7. `wireframe.blank.theme` - Change color scheme for about:blank
8. `wireframe.blank.content` - Remove logo from about:blank
9. `wireframe.controls.reverse` - Reverse window controls
10. `wireframe.toolbar.hide` - Auto hide toolbar buttons (Reveal on hover)
11. `wireframe.navigation.hide` - Disable navigation buttons
12. `wireframe.statusbar.disable` - Disable status bar
13. `wireframe.compact.siderbar.transparent` - Make sidebar transparent in compact mode
14. `zen.theme.essentials-favicon-bg` - Disable favicon background for essentials
15. `wireframe.audio.indicator.disable` - Disable audio indicator on tab

### Dropdown Preferences

1. `wireframe.webview.border-radius` - Border radius for webview (e.g., 0px, 4px, 8px, 12px)
2. `wireframe.macos.controls.radius` - Change macOS window control radius (square, squircle, circle)
3. `wireframe.webview.border_radius` - Border radius for webview (0px, 4px, 8px, 12px, 16px, 20px)
4. `wireframe.window.border_radius` - Border radius for window (0px, 4px, 8px, 12px, 16px, 20px, 24px)
5. `wireframe.tab.border_radius` - Border radius for tabs (0px, 4px, 8px, 12px, 16px, 20px, 24px)
6. `wireframe.essentials.border_radius` - Border radius for essentials (0px, 4px, 8px, 12px, 16px, 20px, 24px, circle)
7. `wireframe.font` - Font selection (SF-Pro, Bricolage, GeistMono, JetBrainsMono, SUSE, SUSEMono)

### String Preferences

1. `wf-border-color` - Change color for window border (currently not working)

## How Preferences Work

  /* Styles when preference is enabled */
  
```

### Implementation Example
For the URL bar position preference, we've implemented a single boolean preference:

- When `wireframe.urlbar.position.top` is enabled, the URL bar appears at the top
- When `wireframe.urlbar.position.top` is disabled (default), the URL bar appears at the bottom

```css
/* URL bar position preference - TOP */
@media (-moz-bool-pref: "wireframe.urlbar.position.top") {
  #zen-appcontent-wrapper {
    flex-direction: column;
  }
}

/* URL bar position preference - BOTTOM (default) */
@media not (-moz-bool-pref: "wireframe.urlbar.position.top") {
  #zen-appcontent-wrapper {
    flex-direction: column-reverse;
  }
}
```

## Adding New Preferences

To add new preferences to the theme:

1. Add the preference definition to `preferences.json`
2. Implement the CSS rules in the appropriate module file
3. Update the README.md file to document the new preference
4. Test the preference to ensure it works correctly

## Preference Best Practices

1. Use descriptive names that clearly indicate what the preference does
2. Provide clear descriptions for each preference
3. Set sensible default values
4. Group related preferences logically
5. Test preferences thoroughly to ensure they work as expected

## New Features in Wireframe 2.0

### Border Radius Controls
Wireframe 2.0 introduces comprehensive border radius controls for different UI elements:
- Webview border radius: Control the corner radius of the web content area
- Window border radius: Adjust the corner radius of the browser window
- Tab border radius: Customize the corner radius of browser tabs
- Essentials border radius: Modify the corner radius of essential UI elements like bookmarks and extensions

### Typography Options
The theme now supports multiple font options with the `wireframe.font` preference:
- SF-Pro: Apple's system font
- Bricolage: Bricolage Grotesque font
- GeistMono: Clean monospace font
- JetBrainsMono: Developer-focused monospace font
- SUSE: Clean sans-serif font
- SUSEMono: Monospace variant of SUSE

### Favicon Background Control
You can now disable the background for favicons in the essentials toolbar using the `zen.theme.essentials-favicon-bg` preference.

### Window Control Radius
Enhanced customization options for macOS style window controls with the `wireframe.macos.controls.radius` preference.

### Fullscreen and Maximized Mode Fixes
Fixed border radius issues when the browser is in fullscreen and maximized modes, ensuring consistent styling across all window states.