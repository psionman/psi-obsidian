## Button
tag: #icon-button 
```python
class Button(ttk.Button):
    """A button with convenience options for layout and enabled state handling.
    It behaves like a standard ttk.Button while tracking whether
    it should dim when disabled.
    """
    def __init__(
            self,
            *args,
            sticky: str = '',
            dimmable: bool = False,
            **kwargs: dict,
            ) -> None:
```
## IconButton
tag: #icon-button
```python
class IconButton(ttk.Frame):
    """A composite button widget that displays both an icon and text 
    in a clickable frame.
    It behaves like a standard button while supporting dimming, 
    custom commands, and flexible layout options.
    """
    def __init__(
            self,
            master,
            button_text,
            icon,
            command=None,
            dimmable: bool = False,
            sticky: str = '',
            icon_path: str = '',
            **kwargs):
            
```
## ButtonFrame
tag: #button-frame
```python
class ButtonFrame(ttk.Frame):
    """A container for managing and laying out 
    groups of buttons with shared state.
    It arranges standard and icon buttons horizontally or 
    vertically and can enable or disable them as a group.
    """
    def __init__(
            self,
            master: tk.Frame,
            orientation: str = tk.HORIZONTAL,
            **kwargs: dict) -> None:
```