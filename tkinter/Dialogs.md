---
aliases: [tkinter dialogs]
tags: "#dialogs"
---
* Yes = True
* No = False
* Cancel = None
## Show
```
messagebox.showinfo("Information","Informative message")
messagebox.showerror("Error", "Error message")
messagebox.sghowwarning("Warning","Warning message")
```
## Yes/No
```answer = messagebox.askokcancel("Question","Do you want to open this file?")
answer = messagebox.askretrycancel("Question", "Do you want to try that again?")
answer = messagebox.askyesno("Question","Do you like Python?")
answer = messagebox.askyesnocancel("Question", "Continue playing?")
```
## Input
```
answer = simpledialog.askstring("Input", "What is your first name?")
answer = simpledialog.askinteger("Input", "What is your age?",
                                 parent=application_window,
answer = simpledialog.askfloat("Input", "What is your salary?",
                               parent=application_window,
                               minvalue=0.0, maxvalue=100000.0)
```
## Files and directories
```
answer = filedialog.askdirectory(parent=application_window,
                                 initialdir=os.getcwd(),
                                 title="Please select a folder:")

# Ask the user to select a single file name.
answer = filedialog.askopenfilename(parent=application_window,
                                    initialdir=os.getcwd(),
                                    title="Please select a file:",
                                    filetypes=my_filetypes)

# Ask the user to select a one or more file names.
answer = filedialog.askopenfilenames(parent=application_window,
                                     initialdir=os.getcwd(),
                                     title="Please select one or more files:",
                                     filetypes=my_filetypes)

# Ask the user to select a single file name for saving.
answer = filedialog.asksaveasfilename(parent=application_window,
                                      initialdir=os.getcwd(),
                                      title="Please select a file name for saving:",
                                      filetypes=my_filetypes)

```
## Colours
```
rgb_color, web_color = colorchooser.askcolor(parent=application_window,
                                             initialcolor=(255, 0, 0))

```
## Yes/No dialog

```python

        dlg = messagebox.askyesno(
            'Delete project',
            f'Are you sure you want to delete {project.name}?',
            parent=self.root,
        )
        if dlg is False:
            return
```

