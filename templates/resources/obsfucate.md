# How to Obfuscate a URL

One method to obsfuscate an URL that shows up on an HTML web page as an anchor link:

- Encode the URL as a Base 64 string
- Place the encoded string into a `<button>` and make it actionable with JavaScript

For example:

When working with a URL, such as `https://pasta.lternet.edu/package/eml/icarus/13/1`, convert it to its Base 64 equivalent  `aHR0cHM6Ly9wYXN0YS5sdGVybmV0LmVkdS9wYWNrYWdlL2VtbC9pY2FydXMvMTMvMQ==` and place it as the data payload of the button:

HTML

```html
<button 
  id="download-btn" 
  data-url="aHR0cHM6Ly9wYXN0YS5sdGVybmV0LmVkdS9wYWNrYWdlL2VtbC9pY2FydXMvMTMvMQ==">
  Download Dataset
</button>
```
JavaScript

```javascript
<script>
  document.addEventListener('DOMContentLoaded', function() {
    const btn = document.getElementById('download-btn');
    if (btn) {
      btn.addEventListener('click', function() {
        const encodedUrl = this.getAttribute('data-url');
        try {
          const realUrl = atob(encodedUrl);
          alert("Decoded URL:\n" + realUrl);
        } catch (e) {
          console.error("Failed to decode Base64 URL:", e);
          alert("Error: Invalid Base64 payload.");
        }
      });
    }
  });
</script>
```

Try me...

<button 
  id="download-btn" 
  data-url="aHR0cHM6Ly9wYXN0YS5sdGVybmV0LmVkdS9wYWNrYWdlL2VtbC9pY2FydXMvMTMvMQ==">
  Download Dataset
</button>

<script>
  document.addEventListener('DOMContentLoaded', function() {
    const btn = document.getElementById('download-btn');
    if (btn) {
      btn.addEventListener('click', function() {
        const encodedUrl = this.getAttribute('data-url');
        try {
          const realUrl = atob(encodedUrl);
          alert("Decoded URL:\n" + realUrl);
        } catch (e) {
          console.error("Failed to decode Base64 URL:", e);
          alert("Error: Invalid Base64 payload.");
        }
      });
    }
  });
</script>