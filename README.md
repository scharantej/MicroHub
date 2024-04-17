## Example 1

**Human:** I need to create a simple Flask web application that allows users to input their names and display a greeting message on a web page.

**Assistant:**

### HTML Files
- **index.html**: This file will contain the HTML markup for the user interface. It will have a form for capturing the user's name and a paragraph tag to display the greeting message.

```html
<!-- index.html -->

<!DOCTYPE html>
<html>
<body>
<h1>Greeting App</h1>
<form action="/greet" method="POST">
    <label for="name">Name:</label>
    <input type="text" name="name">
    <input type="submit" value="Submit">
</form>
<p id="greeting"></p>
</body>
</html>
```

### Routes
- **app.py**: This Python file will contain the code for handling the user request and rendering the appropriate HTML files.

```python
# app.py

from flask import Flask, render_template, request

app = Flask(__name__)

@app.route('/', methods=['GET'])
def index():
    return render_template('index.html')

@app.route('/greet', methods=['POST'])
def greet():
    name = request.form['name']
    greeting = f"Hello, {name}!"
    return render_template('index.html', greeting=greeting)

if __name__ == '__main__':
    app.run()
```