# KvViewer
A different implementation of Kivy's KvViewerApp
# Kivy KV Code Viewer

This application is a tool developed using kivy framework's tool KvViewer. I've changed it so it could allow side-by-side real-time rendering of KV language code. You can write your KV code in a text input field, and the result will be displayed in the second half of the screen.

## Features

- Real-time rendering: The application updates the display as soon as the KV code changes.
- Error handling: If there is an error in the KV code, the application will display the error message instead of the result.

## How to Use

1. Clone this repository to your local machine.
2. Install Kivy if you haven't done so already. Instructions can be found [here](https://kivy.org/doc/stable/installation/installation.html).
3. Run the application by executing the `main.py` (or whatever your main file name is) script with Python.
4. Write your KV code in the left text field. The result will be displayed on the right side of the screen.

## Example

```python
# Paste your final python code here
import textwrap
from kivy.lang import Builder
from kivy.app import App
from kivy.uix.boxlayout import BoxLayout
from kivy.uix.textinput import TextInput
from kivy.uix.label import Label
from kivy.core.window import Window

class KvApp(App):
    def build(self):
        # Set the window size to 1200x800 pixels
        Window.size = (1200, 800)

        self.root = BoxLayout(orientation='horizontal')

        # Create a Text Input for KV code
        self.kv_input = TextInput(size_hint_x=0.5)
        self.kv_input.bind(text=self.update)
        self.root.add_widget(self.kv_input)

        # Create widget placeholder
        self.kv_display = Label(size_hint_x=0.5)
        self.root.add_widget(self.kv_display)

        return self.root


# ... in the KvViewerApp class ...

    def update(self, instance, value)
        self.root.remove_widget(self.kv_display)
        try:
            # Use textwrap.dedent on value to remove any common leading whitespace
            self.kv_display = Builder.load_string(textwrap.dedent(value))
            self.kv_display.size_hint_x = 0.5
            self.root.add_widget(self.kv_display)
        except Exception as e:
            self.kv_display = Label(text=str(e), size_hint_x=0.5)
            self.root.add_widget(self.kv_display)

if __name__ == '__main__':
    KvApp().run()

## Credits

This project was built using the [Kivy](https://kivy.org/#home) open source Python library for developing multitouch applications. It's a community project and wouldn't exist without the support and dedication of many individuals. I'd like to thank the Kivy community for their valuable contributions and for making such a powerful tool available to developers.

