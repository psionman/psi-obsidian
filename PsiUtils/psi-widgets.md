## PsiText
???
## Get Styles
tag: #styles 
Style definitions; usage, in *root.py*:
```python
get_styles()
```
## Status bar
tag: #status-bar
```python
def status_bar(master: tk.Frame, textvariable: tk.StringVar, colour: str = DIM_TEXT) -> tk.Frame:
	"""Create a simple status bar frame with a single label.
	The status bar displays text from a StringVar
	and can be styled with a custom foreground colour.
	"""
```
## Seperator frame

tag: #seperator-frame
```python
def separator_frame(master: tk.Frame, text: str) -> tk.Frame:
	"""Create a labelled separator frame with horizontal lines on either side.
		This widget visually separates sections of a layout
		while displaying a short label.
	"""
```
## Vertical scrolled frame
tag: #scrolled-frame
```python
class VerticalScrolledFrame(ttk.Frame):
    """A frame that provides a vertically scrollable canvas for child widgets.
        This allows embedding a large number of widgets in a 
        constrained vertical space with automatic scrollbar handling.
    """
    def __init__(self, parent, *args, **kw):
		ttk.Frame.__init__(self, parent, *args, **kw)
		self.rowconfigure(0, weight=1)	
		self.columnconfigure(0, weight=1)
```
## Tooltip
tag: #tool-tip
```python
class Tooltip:
    """A tooltip helper that displays contextual text 
        when hovering over a widget.
        It shows a small window near the mouse cursor after a delay 
        and hides it when the cursor leaves.
    """
    def __init__(self, widget,
                 *,
                 bg='#FFFFEA',
                 pad=(5, 3, 5, 3),
                 text='',
                 textvariable=None,
                 wait_time=400,
                 wrap_length=250,
                 vertical_offset=0,):
```
## Date picker
tag: #date-picker
```python
class DatePicker(tk.Frame):
    """A compact widget for selecting and incrementing calendar dates.
        It displays a date entry field with up and down buttons to 
        adjust the selected day.
    """
    def __init__(
            self, master: tk.Frame,
            initial_date: datetime = None,
            date_format: str = ''):
```
## Time picker
tag: #time-picker
```python
class TimePicker(tk.Frame):
    """A compact widget for selecting a time value using incrementable fields.
    It lets users adjust hours, minutes, and optionally seconds 
    with arrow buttons and combo boxes.
    """
    def __init__(
            self, master: tk.Frame,
            use_seconds: bool = False,
            use_labels: bool = False):
```
