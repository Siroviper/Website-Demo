# How to Create and Manage Your Blog Posts

This guide will show you how to create new blog posts and manage your content on your blog.

## File Structure

Your blog uses a simple structure:
```
Blog/
├── blogs/                          # All blog posts go here
│   ├── example-blog-post.html      # The HTML template
│   ├── example-blog-post.txt       # The actual content
│   └── [your-post-name].html       # New posts
│   └── [your-post-name].txt        # New content files
├── blog.html                       # Main blog listing page
└── ...other files
```

---

## Creating a New Blog Post

### Step 1: Create the Content File (.txt)

1. Navigate to the `blogs/` folder
2. Create a new `.txt` file with your post name (e.g., `my-second-post.txt`)
3. Format your content like this:

```
Title of Your Blog Post

> Posted: [Date]

Your introduction paragraph goes here.

## Section Heading

Your content here. You can use Markdown formatting:
- **Bold text**
- *Italic text*
- Lists
- [Links](http://example.com)

## Another Section

More content...
```

**Important Formatting Rules:**
- First line = Your blog title (H1)
- Use `>` for metadata like date
- Use `##` for section headings (H2)
- Separate paragraphs with blank lines

### Step 2: Create the HTML File

1. **Copy** `example-blog-post.html` in the `blogs/` folder
2. **Rename** it to match your content file (e.g., `my-second-post.html`)
3. **Edit** the HTML file:
   - Change the `<title>` tag (line 7) to your post title
   - Change the fetch URL (line 164) to your txt filename:
     ```javascript
     fetch('my-second-post.txt')  // Change this line
     ```

That's it! Your blog post is ready.

---

## Adding Blog Post to the Blog Listing Page

To make your new post appear on the main blog page:

1. Open `blog.html` (in the root Blog folder, not in blogs/)
2. Find the `<ul>` list section (around line 127)
3. Add a new list item:

```html
<li style="margin-bottom: 10px;">
    <span style="color: var(--accent-blue); margin-right: 10px;">> [Date]:</span>
    <a href="blogs/my-second-post.html" style="color: var(--link-color); text-decoration: underline;">
        Your Post Title Here
    </a>
</li>
```

---

## Quick Reference: Supported Markdown

Your `.txt` content files support these Markdown features:

- **Headings**: `##` for H2, `###` for H3
- **Bold**: `**text**`
- **Italic**: `*text*`
- **Links**: `[text](url)`
- **Lists**: Start lines with `-` or `*`
- **Blockquotes**: Start lines with `>`
- **Code**: Use backticks \`code\`

---

## Example Workflow

Let's say you want to create a blog post about your favorite books:

1. **Create** `blogs/favorite-books.txt`:
```
My Favorite Books of 2025

> Posted: November 20, 2025

Here are some books I loved this year...

## Fiction
- Book 1
- Book 2

## Non-Fiction
- Book 3
```

2. **Copy** `blogs/example-blog-post.html` to `blogs/favorite-books.html`

3. **Edit** `favorite-books.html`:
   - Line 7: `<title>My Favorite Books of 2025</title>`
   - Line 164: `fetch('favorite-books.txt')`

4. **Update** `blog.html` with new entry:
```html
<li style="margin-bottom: 10px;">
    <span style="color: var(--accent-blue); margin-right: 10px;">> 2025-11-20:</span>
    <a href="blogs/favorite-books.html" style="color: var(--link-color); text-decoration: underline;">
        My Favorite Books of 2025
    </a>
</li>
```

Done! Your new post is live.

---

## Important Notes

⚠️ **Local Server Required**: Because the blog posts use JavaScript `fetch()` to load content, you need to run a local web server. Opening the HTML files directly with `file://` won't work in most browsers.

**Options for running a local server:**
- VS Code: Install "Live Server" extension
- Python: `python -m http.server` in the Blog folder
- Node.js: `npx serve`

💡 **Tips:**
- Keep .txt filenames simple (use hyphens, not spaces)
- Always match the .html and .txt filenames
- Test your post on a local server before deploying
- Backup your content files regularly

---

## Troubleshooting

**Problem**: "Error Loading Blog Post" message
- **Solution**: Make sure you're running a local server and the .txt file exists

**Problem**: Formatting looks wrong
- **Solution**: Check your Markdown syntax, ensure blank lines between paragraphs

**Problem**: New post doesn't show on blog.html
- **Solution**: Make sure you added the list item to blog.html and the path is correct

---

That's all you need to know! Happy blogging! 📝
