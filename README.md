# Basic2PlayerChess
The project was created as a hobby in 2019. It is a simple two-player chess game in C#. 
It just need to be loaded into C# IDE and run!


# Works in more places on GitHub
- **Issues / PRs / Discussions / Wikis**: same ` ```mermaid ` block works—great for design threads and RFCs.

# Tips that avoid breakage
- Use `<br/>` for line breaks inside nodes (GitHub’s renderer prefers it over `\n`).  
- Escape `<` as `&lt;` (already done for “\<200nm”).  
- Very long labels? Add `<br/>` line breaks to prevent overflow.  
- If it shows as plain text, double-check the fence: it must start with three backticks + `mermaid` and end with three backticks.

# GitHub Pages (optional)
- **README on repo homepage renders Mermaid automatically.**  
- If you’re building a separate **GitHub Pages site** with custom HTML/Markdown and you want Mermaid there, the most reliable route is to:
  - Create an HTML page, include Mermaid JS:
    ```html
    <script type="module">
      import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@10/dist/mermaid.esm.min.mjs';
      mermaid.initialize({ startOnLoad: true, securityLevel: 'strict' });
    </script>
    ```
  - Put your diagram in a `<pre class="mermaid">...</pre>` block on that page.

# Exporting to images (if you want a static asset)
- Use the **“Markdown Preview Mermaid Support”** or **“Markdown Preview Enhanced”** extension in VS Code to export PNG/SVG, then commit the image and reference it in your README:
  ```markdown
  ![Pipeline](assets/pipeline.svg)
