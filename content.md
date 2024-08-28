# HTML, CSS, and ERB Style Basics

## Introduction
When developing web applications, adhering to proper HTML, CSS, and ERB style conventions is crucial. Clean and consistent code not only improves readability and maintainability but also ensures that your application behaves as expected across different browsers and environments. In this lesson, you will learn the fundamentals of HTML, CSS, and ERB style, including best practices for structuring your code, naming conventions, and using Visual Studio Code (VSCode) to format your files.

## Objectives
By the end of this lesson, you will be able to:

- Understand and apply proper HTML and CSS conventions.
- Utilize ERB templates effectively in Ruby Sinatra applications.
- Use the "Format Document" feature in VSCode to automatically format your HTML and CSS code.
- Recognize and avoid common style mistakes in HTML, CSS, and ERB.

## HTML Style Basics

### HTML Conventions
HTML is the backbone of web pages. Following consistent conventions helps make your markup easier to read and maintain.

### Structure and Indentation
- **Tags and Elements**: Use lowercase for all `<html>` tags.
- **Indentation**: Use 2 spaces per indentation level. Do not use tabs or mix spaces and tabs.

```html
<!DOCTYPE html>
<html>
  <head>
    <title>My Sinatra App</title>
  </head>
  <body>
    <h1>Welcome to My Sinatra App</h1>
    <p>This is a sample paragraph.</p>
  </body>
</html>
```

### Attribute Formatting
- **Quotes**: Always use double quotes `"` for attribute values.
- **Boolean Attributes**: Omit the value for boolean attributes (e.g., `checked`, `disabled`).

```html
<input type="checkbox" checked>
<a href="https://example.com" target="_blank">Visit Example</a>
```

### Self-Closing Tags
In HTML5, self-closing tags like `<br>`, `<img>`, and `<input>` do not require a closing slash.

```html
<img src="image.png" alt="Sample Image">
```

### Casing
- **Classes and IDs**: Use `kebab-case`, where words are lowercase and separated by hyphens. Example:

```html
<div>
  <h1 id="main-title">Main Title</h1>
  <p class="main-description">A long description</p>
</div>
```

- **File and Folder Names**: Use lowercase letters and separate words with hyphens for HTML files and folders. This convention is widely accepted and makes URLs easier to read and type. Examples: `index.html`, `contact-us.html`, `css/`, `images/`.

<!--  -->

- What is the correct indentation for HTML?
- 1 space
  - Not quite. HTML requires more space for proper indentation.
- 2 spaces
  - Correct! HTML typically uses 2 spaces per indentation level.
- 4 spaces
  - Not quite. While some styles use 4 spaces, the standard for HTML in this course is 2 spaces.
{: .choose_best #html_indentation title="HTML Indentation" points="1" answer="2" }

## CSS Style Basics

### CSS Conventions
CSS (Cascading Style Sheets) controls the presentation of your web pages. Following consistent styling practices in CSS helps you manage and maintain your stylesheets effectively.

### Formatting and Indentation
- **Selectors**: Write each selector on a new line, separated by commas.
- **Properties**: Use a colon followed by a space before the value. Each property should be on its own line, ending with a semicolon.
- **Indentation**: Use 2 spaces for indentation within rule sets.

```css
body {
  font-family: Arial, sans-serif;
  color: #333;
}

h1,
h2,
h3 {
  margin-bottom: 10px;
}
```

### Avoid Inline Styles
Avoid using inline styles (styles defined directly in the HTML elements using the style attribute) as they make your HTML hard to maintain and can override your external CSS. Always keep your CSS in separate files for better maintainability and reusability.

```html
<!-- Avoid this: -->
<p style="color: red;">This is a paragraph.</p>

<!-- Use this instead: -->
<p class="text-red">This is a paragraph.</p>
```

```css
/* with this style rule */
.text-red {
  color: red;
}
```

### Casing
- **Class Names and IDs**: Use `kebab-case` (lowercase letters, separated by hyphens) for class names and IDs.
- **Files and Folder Names**: Use lowercase letters and hyphens for CSS file names. Examples: `styles.css`, `main-styles.css`.

```css
.button-primary {
  background-color: #007bff;
  color: #fff;
}
```

- What is the correct naming convention for CSS class names?
- `camelCase`
  - Not quite. `camelCase` is commonly used in JavaScript.
- `snake_case`
  - Not quite. `snake_case` is often used in Ruby.
- `kebab-case`
  - Correct! CSS class names should use `kebab-case`.
{: .choose_best #css_naming title="CSS Naming Conventions" points="1" answer="3" }

## ERB Style Basics

### ERB Conventions
Embedded Ruby (ERB) allows you to embed Ruby code within HTML. Proper use of ERB is essential for clean and maintainable Sinatra applications.

### Syntax and Spacing
- **ERB Tags**: Use `<%= %>` for Ruby expressions that return a value and `<% %>` for expressions that do not return a value.
- **Spacing**: Include a space inside the ERB tags for readability. Examples: `<% good %>` and `<%bad%>`

```erb
<%= @user.name %>

<% if @user.admin? %>
  <p>Welcome, admin!</p>
<% end %>
```

### Casing
- **File and Folder Naming**: ERB files should use `snake_case`, similar to Ruby files, with a `.html.erb` extension. Examples: `user_profile.html.erb`, `index.html.erb`.

### Logic and Presentation Separation
Keep Ruby logic out of your views as much as possible. Use helper methods in your Sinatra app to maintain separation of concerns.

```ruby
# In your Sinatra app (app.rb)
helpers do
  def format_date(date)
    date.strftime("%B %d, %Y")
  end
end
```

```erb
<!-- In your ERB template (index.erb) -->
<p><%= format_date(Date.today) %></p>
```

- Which ERB tag is used for Ruby expressions that do not return a value?
- `<%= %>`
  - Not quite. `<%= %>` is used for expressions that return a value.
- `<% %>`
  - Correct! `<% %>` is used for Ruby code that does not output a value.
- `<%== %>`
  - Not quite. `<%== %>` is not a standard ERB tag.
{: .choose_best #erb_syntax title="ERB Tag Usage" points="1" answer="2" }

## Using Format Document in VSCode
VSCode's "Format Document" feature is a powerful tool that automatically formats your code according to the style guidelines of the language you're working with.

### Set Up Formatting for HTML and ERB
Ensure that you have the appropriate formatter installed for HTML and ERB. For ERB, the [htmlbeautifier gem](https://github.com/threedaymonk/htmlbeautifier) and the [ERB Formatter/Beautify VSCode extension](https://marketplace.visualstudio.com/items?itemName=aliariff.vscode-erb-beautify) are popular choices.

#### Install htmlbeautifier
To install htmlbeautifier, run the following command in your terminal:

```bash
gem install htmlbeautifier
```

#### Install ERB Formatter/Beautify VSCode Extension
To install the ERB Formatter/Beautify extension:

##### Open VSCode.
- Go to the Extensions view by clicking on the square icon in the sidebar or pressing Ctrl + Shift + X (Windows/Linux) or Cmd + Shift + X (Mac).
- Search for "ERB Formatter/Beautify" and click Install.

#### Use Format Document
To format your html.erb files manually:

##### 1. Open the file you want to format in VSCode.

##### 2. Format Document:
- Right-click anywhere in the editor and select Format Document from the context menu.
- Use the keyboard shortcut Shift + Alt + F (Windows) or Shift + Option + F (Mac) to format the document.
- Search "Format Document" from the command palette CTRL + Shift + P (Windows) or Command + Shift + P (Mac).

##### 3. VSCode will automatically format the document based on the settings you've configured.

- Which command in VSCode formats the entire document?
- Ctrl + S
  - Not quite. This command saves the file but does not format it.
- Shift + Alt + F (Windows) / Shift + Option + F (Mac)
  - Correct! This command formats the entire document.
- Ctrl + F
  - Not quite. This command is used for finding text in the document.
{: .choose_best #vs_code_format title="Formatting Document" points="1" answer="2" }

## Best Practices

### Consistency is Key
Consistency in your coding style makes your code easier to read and maintain. Whether you're working on a team or on a solo project, follow these best practices:

- **Stick to the style guide**: Following a consistent style guide is crucial.
- **Use tools to automate**: Use formatters like "Format Document" in VSCode to automatically enforce your style guide.
- **Review and Refactor**: Regularly review your code and refactor it to meet the style guidelines.

<!--  -->

- Why is consistency in coding style important?
- It makes the code prettier.
  - Not quite. While prettier code is a side benefit, there's a more important reason.
- It helps in debugging.
  - Partially correct. Consistent code can make debugging easier, but there’s a broader reason.
- It makes the code easier to read and maintain.
  - Correct! Consistency helps in readability and maintainability of the code.
{: .choose_best #consistency_importance_html title="Importance of Consistency" points="1" answer="3" }

## Conclusion
This lesson provides the foundation for writing clean and consistent HTML, CSS, and ERB in your Ruby Sinatra applications. By adhering to these guidelines and utilizing tools like VSCode’s "Format Document" feature, you'll improve your coding skills and ensure that your code is easy to read, maintain, and share with others.

---

- Approximately how long (in minutes) did this lesson take you to complete?
{: .free_text_number #time_taken_html title="Time taken" points="1" answer="any" }
