# Mini Note Website

A beautiful landing page for the Mini Note Chrome Extension.

## 📁 Files

- `index.html` - Main landing page
- `documentation.html` - User documentation
- `release-notes.html` - Version history
- `privacy-policy.html` - Privacy policy
- `logo.png` - Extension icon

---

## 🔧 How to Configure Google Forms for Contact Form

Follow these steps to connect the contact form to Google Forms:

### Step 1: Create a Google Form

1. Go to [Google Forms](https://forms.google.com)
2. Click **"+ Blank"** to create a new form
3. Add three questions:
   - **Question 1:** "Full Name" (Short answer)
   - **Question 2:** "Email" (Short answer)
   - **Question 3:** "Comments" (Paragraph)

### Step 2: Get the Form URL

1. Click the **"Send"** button in Google Forms
2. Click the **link icon** (🔗)
3. Copy the URL (it looks like: `https://docs.google.com/forms/d/e/FORM_ID/viewform`)

### Step 3: Get the Form Action URL

1. From your form URL, change `viewform` to `formResponse`
2. Your action URL will look like:
   ```
   https://docs.google.com/forms/d/e/FORM_ID/formResponse
   ```

### Step 4: Get Entry IDs for Each Field

1. In Google Forms, click the **three dots menu (⋮)** → **"Get pre-filled link"**
2. Fill in sample data for each field and click **"Get link"**
3. Copy the generated URL and look for the entry IDs:
   ```
   https://docs.google.com/forms/d/e/FORM_ID/viewform?entry.123456789=SampleName&entry.987654321=sample@email.com&entry.456789123=SampleComment
   ```
4. Note down each `entry.XXXXXXXXX` number for each field

### Step 5: Update the HTML

Open `index.html` and find the contact form section. Replace the placeholders:

```html
<!-- Find this line and replace YOUR_GOOGLE_FORM_URL -->
<form id="contactForm" action="YOUR_GOOGLE_FORM_URL" method="POST" target="hidden_iframe">

<!-- Replace with your actual URL -->
<form id="contactForm" action="https://docs.google.com/forms/d/e/YOUR_FORM_ID/formResponse" method="POST" target="hidden_iframe">
```

Then update each input field's `name` attribute:

```html
<!-- Full Name field -->
<input type="text" id="fullName" name="entry.YOUR_FULLNAME_ENTRY_ID" ...>

<!-- Email field -->
<input type="email" id="email" name="entry.YOUR_EMAIL_ENTRY_ID" ...>

<!-- Comments field -->
<textarea id="comments" name="entry.YOUR_COMMENTS_ENTRY_ID" ...></textarea>
```

### Example Configuration

Here's an example of what your form might look like after configuration:

```html
<form id="contactForm" action="https://docs.google.com/forms/d/e/1FAIpQLSf8xyz123abc/formResponse" method="POST" target="hidden_iframe">
    <div class="form-group">
        <label for="fullName">Full Name</label>
        <input type="text" id="fullName" name="entry.1234567890" placeholder="John Doe" required>
    </div>
    <div class="form-group">
        <label for="email">Email Address</label>
        <input type="email" id="email" name="entry.0987654321" placeholder="john@example.com" required>
    </div>
    <div class="form-group">
        <label for="comments">Comments</label>
        <textarea id="comments" name="entry.1122334455" placeholder="Your message here..." rows="4" required></textarea>
    </div>
    ...
</form>
```

### Step 6: Test Your Form

1. Open your website locally or deploy it
2. Fill out the contact form and submit
3. Check your Google Form responses to verify data is being received

---

## 🚀 Deployment

### GitHub Pages

1. Create a new repository on GitHub
2. Upload all files to the repository
3. Go to **Settings** → **Pages**
4. Select source branch (usually `main`)
5. Your site will be live at `https://yourusername.github.io/repository-name/`

### Netlify

1. Go to [Netlify](https://netlify.com)
2. Drag and drop your project folder
3. Your site will be live instantly!

---

## 📝 Customization

### Change Extension Install Link

Find this line in `index.html` and replace with your Chrome Web Store URL:

```html
<a href="#" class="btn btn-primary">
```

Change to:

```html
<a href="https://chromewebstore.google.com/detail/your-extension-id" class="btn btn-primary">
```

### Update Contact Email

In `privacy-policy.html`, find and update:

```html
<p><strong>Email:</strong> privacy@mininote.app</p>
```

---

## 📄 License

© 2025 Mini Note. All rights reserved.
