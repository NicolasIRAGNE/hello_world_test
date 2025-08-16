# Popek Language Specification

This project should be entirely written in Popek.

## Overview
Popek is a simple, declarative programming language designed for creating basic GUI applications with buttons, text, and simple user interfaces. It emphasizes readability and ease of use for building interactive desktop applications.

## File Extension
- `.ppk` - Popek source files

## Directory Structure
```
my-app/
├── main.ppk           # Entry point (required)
├── components/        # Reusable UI components
│   ├── button.ppk
│   └── dialog.ppk
├── styles/           # Style definitions
│   └── theme.ppk
├── assets/           # Static resources
│   ├── images/
│   └── fonts/
└── config.ppk        # App configuration (optional)
```

## Language Syntax

### Basic Structure
Every Popek application starts with `main.ppk` containing an `app` block:

```popek
app "My Application" {
    window {
        title: "Hello World"
        width: 800
        height: 600
        
        # UI components go here
    }
}
```

### Data Types

#### Primitives
- `text` - String values: `"hello world"`
- `number` - Integers and decimals: `42`, `3.14`
- `bool` - Boolean values: `true`, `false`
- `color` - Color values: `#FF0000`, `red`, `rgb(255,0,0)`

#### Collections
- `list` - Ordered collection: `[1, 2, 3]`
- `map` - Key-value pairs: `{name: "John", age: 25}`

### Variables
```popek
let message = "Hello World"
let count = 0
let isVisible = true
```

### UI Components

#### Window
```popek
window {
    title: "App Title"
    width: 800
    height: 600
    resizable: true
    centered: true
}
```

#### Button
```popek
button "Click Me" {
    width: 100
    height: 30
    background: blue
    color: white
    
    onclick: {
        # Action code here
    }
}
```

#### Text
```popek
text message {
    size: 16
    color: black
    bold: false
    align: left
}
```

#### Input
```popek
input userInput {
    placeholder: "Enter text..."
    width: 200
    height: 25
    
    onchange: {
        # Handle input change
    }
}
```

#### Container
```popek
container {
    layout: vertical  # or horizontal, grid
    padding: 10
    spacing: 5
    
    # Child components
}
```

### Layout Types
- `vertical` - Stack components vertically
- `horizontal` - Arrange components horizontally  
- `grid` - Grid layout with rows/columns
- `absolute` - Absolute positioning

### Events and Actions

#### Event Types
- `onclick` - Mouse click
- `onchange` - Value change
- `onload` - Component loaded
- `onclose` - Window closing

#### Actions
```popek
# Set variable value
set count = count + 1

# Show/hide components
show myButton
hide myDialog

# Update component properties
update myText.content = "New text"
update myButton.background = red

# Navigate between views
goto "settings"

# Exit application
exit
```

### Functions
```popek
function calculateSum(a, b) {
    return a + b
}

function showMessage(msg) {
    dialog {
        title: "Message"
        content: msg
        
        button "OK" {
            onclick: { close }
        }
    }
}
```

### Conditional Logic
```popek
if count > 10 {
    update status.content = "High count"
} else {
    update status.content = "Low count"
}
```

### Loops
```popek
# For loop
for i in 1 to 10 {
    # Loop body
}

# For each loop
for item in myList {
    # Process each item
}
```

### Imports
```popek
import "components/button.ppk"
import "styles/theme.ppk" as theme
```

## Complete Example

### main.ppk
```popek
app "Counter App" {
    let count = 0
    
    window {
        title: "Simple Counter"
        width: 300
        height: 200
        centered: true
        
        container {
            layout: vertical
            padding: 20
            spacing: 10
            
            text countDisplay {
                content: "Count: " + count
                size: 18
                align: center
            }
            
            container {
                layout: horizontal
                spacing: 10
                
                button "+" {
                    width: 50
                    height: 30
                    background: green
                    color: white
                    
                    onclick: {
                        set count = count + 1
                        update countDisplay.content = "Count: " + count
                    }
                }
                
                button "-" {
                    width: 50
                    height: 30
                    background: red
                    color: white
                    
                    onclick: {
                        set count = count - 1
                        update countDisplay.content = "Count: " + count
                    }
                }
                
                button "Reset" {
                    width: 60
                    height: 30
                    background: gray
                    color: white
                    
                    onclick: {
                        set count = 0
                        update countDisplay.content = "Count: " + count
                    }
                }
            }
        }
    }
}
```

### components/dialog.ppk
```popek
component AlertDialog(title, message) {
    dialog {
        title: title
        width: 250
        height: 150
        modal: true
        
        container {
            layout: vertical
            padding: 15
            spacing: 10
            
            text {
                content: message
                align: center
            }
            
            button "OK" {
                width: 80
                height: 25
                background: blue
                color: white
                
                onclick: { close }
            }
        }
    }
}
```

## Styling

### Inline Styles
Properties can be set directly on components:
```popek
button "Styled Button" {
    background: #4CAF50
    color: white
    border: none
    borderRadius: 5
    fontSize: 14
}
```

### Style Sheets
Create reusable styles in `.ppk` files:

```popek
# styles/theme.ppk
style primaryButton {
    background: #2196F3
    color: white
    border: none
    borderRadius: 4
    padding: 8
}

style headerText {
    fontSize: 20
    fontWeight: bold
    color: #333
}
```

Apply styles using the `style` property:
```popek
button "Primary" {
    style: primaryButton
}
```

## Comments
```popek
# Single line comment

#*
Multi-line
comment
*#
```

## Error Handling
```popek
try {
    # Code that might fail
    let result = divide(10, 0)
} catch error {
    showMessage("Error: " + error.message)
}
```

## Configuration

### config.ppk
```popek
config {
    appName: "My Popek App"
    version: "1.0.0"
    author: "Developer Name"
    
    window {
        defaultWidth: 800
        defaultHeight: 600
        minWidth: 400
        minHeight: 300
    }
    
    theme: "light"  # or "dark"
}
```

## Built-in Functions

### String Functions
- `length(text)` - Get string length
- `substring(text, start, end)` - Extract substring
- `uppercase(text)` - Convert to uppercase
- `lowercase(text)` - Convert to lowercase

### Math Functions
- `abs(number)` - Absolute value
- `round(number)` - Round to nearest integer
- `random()` - Random number 0-1
- `min(a, b)` - Minimum value
- `max(a, b)` - Maximum value

### List Functions
- `add(list, item)` - Add item to list
- `remove(list, index)` - Remove item at index
- `size(list)` - Get list size
- `contains(list, item)` - Check if list contains item

## Runtime Requirements
- Popek applications compile to native executables
- Cross-platform support (Windows, macOS, Linux)
- Minimal runtime dependencies
- Hot-reload support during development

## Development Tools
- `popek build` - Compile application
- `popek run` - Run in development mode
- `popek package` - Create distributable package
- `popek format` - Format source code

This specification provides a complete foundation for building simple GUI applications with buttons, text, input fields, and basic user interactions while maintaining simplicity and readability.