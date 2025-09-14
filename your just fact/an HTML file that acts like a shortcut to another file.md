If you want an HTML file that acts like a **shortcut to another file** (for example, a document, image, video, or even another website), you can create an HTML file that automatically redirects or provides a clickable link to that file.

### ✅ Option 1: **Automatic Redirect**

This version automatically redirects the user to the target file when they open the HTML file.

```html
<!DOCTYPE html>
<html>
<head>
  <meta http-equiv="refresh" content="0; url=target-file.pdf">
  <title>Redirecting...</title>
</head>
<body>
  <p>If you are not redirected automatically, <a href="target-file.pdf">click here</a>.</p>
</body>
</html>
```

> 🔁 Replace `target-file.pdf` with the actual filename or path (relative or absolute) to the file.

---

### ✅ Option 2: **Clickable Shortcut Link**

If you want the user to click a link to open the file:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Open File</title>
</head>
<body>
  <h2>Open File Shortcut</h2>
  <p><a href="target-file.pdf" target="_blank">Click here to open the file</a></p>
</body>
</html>
```

---

### ✅ Notes:

* If the file is **on the same directory**, you can just use the filename (e.g. `document.docx`).
* If it's in a **subfolder**, use something like `files/document.docx`.
* If it's an **external file** on the web, use the full URL like `https://example.com/file.pdf`.
* For **local files**, web browsers often **won’t allow direct access** (due to security). You’d need to open the HTML file in a trusted environment (like locally via a browser) or use a web server.
