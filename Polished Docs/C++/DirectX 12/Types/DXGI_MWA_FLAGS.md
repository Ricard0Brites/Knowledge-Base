# DXGI_MWA_FLAGS

The `DXGI_MWA_FLAGS` are used with the `IDXGIFactory::MakeWindowAssociation` method to control how DXGI (DirectX Graphics Infrastructure) responds to certain window messages and behaviors, particularly concerning input and automatic mode changes.

---

## Flags

| Flag                       | Value | Description                                                                                                                               |
|----------------------------|-------|-------------------------------------------------------------------------------------------------------------------------------------------|
| `DXGI_MWA_NO_WINDOW_CHANGES` | 1     | Prevents DXGI from automatically changing the window's style, position, or size. This is useful when the application wants full control over its window management. |
| `DXGI_MWA_NO_ALT_ENTER`      | 2     | Disables the default behavior of toggling between windowed and fullscreen mode when the user presses `Alt+Enter`. Most games and applications handle this transition manually. |
| `DXGI_MWA_NO_PRINT_SCREEN`   | 4     | Prevents DXGI from handling the `Print Screen` key. By default, DXGI would capture the screen, but this flag disables that behavior, allowing the application to implement its own screenshot logic or to block it entirely. |
| `DXGI_MWA_NO_WINDOW_KEYBOARD_INPUT` | | When this flag is set, DXGI prevents the application from receiving keyboard input. This is typically used in full-screen applications or games where the application takes over keyboard handling directly. |
| `DXGI_MWA_NO_WINDOW_MOUSE_INPUT` | | This flag, when set, prevents the application from receiving mouse input. Similar to the keyboard input flag, this is useful for applications that manage mouse input directly. |

**Note**: The values for `DXGI_MWA_NO_WINDOW_KEYBOARD_INPUT` and `DXGI_MWA_NO_WINDOW_MOUSE_INPUT` are not explicitly defined in the public headers but are reserved for internal use. Their behavior might not be consistent across all versions of Windows.
