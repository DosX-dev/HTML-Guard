# 🛢 HTML Guard
When you add the static module `html-guard.js` it will automatically obfuscate the page layout. Protect your web application/site.

⚙️📄 __Makes it possible to use dynamic loading of resources using built-in functions, which prevents static downloading of styles and scripts.__

Briefly about the functions of HTML Guard:
 * 🛡 Obfuscation of HTML (auto)
 * 🛡🛠 Dynamic adding of CSS/JS (requires setup)
 * 🛡 Blocking DevTools in any browsers
 * 🛡 Lock the context menu
 * 🛡 Block dragging from a page
 * 🛡 Block text selection on a page
 * 🛡 Block console output

![](screenshots/devtools.jpg)

## 🔧 Add it to your site
```html
<!DOCTYPE  html>
<html>
    <head>
        <!-- Site protection ON! -->
        <script src="html-guard.js"></script>
        <script>
            // Configure protection & resource loading
        </script>
    </head>

    <body>
    </body>
</html>
```

## ✅ Configure

### ⚙️🔴 Safe style/script adding
Avoid using `<link>`. Dynamically load .css and .js files! This method makes it possible to bypass downloaders of sites such as [web2zip.com](https://web2zip.com/). Dynamic addition of site resources makes it impossible to copy them during static analysis.
And in this case, when HTML Guard is removed from the dependencies, the contents of the web application will not be able to load for obvious reasons.

```html
<script>
    // ADDING: Add link to 'style.css'
    HtmlGuard.loader.loadStyleByRef("styles.css");
</script>
```

```html
<script>
    // ADDING: Add script "test.js" to head
    HtmlGuard.loader.loadScriptBySrc("test.js");

    //  OR

    // ADDING: Add script "test.js" to head after document loading
    HtmlGuard.loader.loadScriptBySrc_ContentLoaded("test.js");
</script>
```

### 🔒✨ Block Dev-Tools (recommended)
This function blocks any attempts to open developer tools and, if detected, reloads the page.
```html
<script>
    // PROTECTION: Disable DevTools
    HtmlGuard.protections.antiDevTools();
</script>
```

### 🔒 Disable context menu
Blocks the opening of the standard context menu.
```html
<script>
    // PROTECTION: Disable context menu
    HtmlGuard.protections.blockContextMenu();
</script>
```

### 🔒 Disable drag
The user will not be able to drag elements from the site.
```html
<script>
    // PROTECTION: Disable drag
    HtmlGuard.protections.blockDrag();
</script>
```

### 🔒 Disable selection
Removes the ability to use selection.
```html
<script>
    // PROTECTION: Disable selection
    HtmlGuard.protections.blockSelection();
</script>
```

### 🔒 Disable console output
This will be useful for hiding debug logs from the browser console. Hooks functions such as `log`, `debug`, `warn`, `error`, `dir`, `dirxml`, `assert`, `table` making them return __null__
```html
<script>
    // PROTECTION: Disable console output
    HtmlGuard.protections.blockConsoleOutput();
</script>
```

## 📄 Example of using
```html
<!-- Example of HTML-Guard protection -->

<!DOCTYPE html>
<html>

<head>
    <script src="../html-guard.js"></script>
    <script>
        // PROTECTION: Disable DevTools
        HtmlGuard.protections.antiDevTools();

        // PROTECTION: Disable context menu
        HtmlGuard.protections.blockContextMenu();

        // PROTECTION: Disable drag
        HtmlGuard.protections.blockDrag();

        // PROTECTION: Disable selection
        HtmlGuard.protections.blockSelection();

        // PROTECTION: Disable console output
        HtmlGuard.protections.blockConsoleOutput();


        // ADDING: Add link to 'style.css'
        HtmlGuard.loader.loadStyleByRef("styles.css");

        // ADDING: Run 'test.js' script
        HtmlGuard.loader.loadScriptBySrc("test.js");
    </script>
</head>

<body>
    <div>
        <p>Hello, world!</p>
    </div>
</body>

</html>
```
