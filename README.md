# [Miranda Abi Tazi]

> ["Web development learner focused on building clean, responsive, and user-friendly websites using HTML, CSS, and JavaScript. Passionate about improving my skills through continuous practice and real projects."]

**This is a learning project.** Every file is intentionally incomplete. Your job is to open each one, understand it, and make it your own. If a file works without you touching it, we didn't do our job right - [let us know]([link-to-issues]).

---

## Table of Contents

- [What You Will Learn](#what-you-will-learn)
- [What You Need Before Starting](#what-you-need-before-starting)
- [Getting Started](#getting-started)
- [The Big Picture - How It All Fits Together](#the-big-picture--how-it-all-fits-together)
- [Project Files Explained](#project-files-explained)
- [Your Tasks - Step by Step](#your-tasks--step-by-step)
- [Going Further](#going-further)
- [License](#license)

---

## What You Will Learn

By finishing this project you will practice:

| Skill | Where you use it |
|---|---|
| Basic HTML structure & tags | `index.html`, `test.html`, `models/` |
| Styling with CSS (colours, layout, fonts) | `assets/css/style.css` |
| Making pages interactive with JavaScript | `assets/js/script.js` |
| Handling form data with PHP | `generate.php` (you create this) |
| Connecting to a database with PHP | `config/database.php` (you create this) |
| Writing SQL to create and query tables | `config/schema.sql` |
| Using environment variables (`.env`) | Project root |
| Deploying a web app to a server | Your live site |

---

## What You Need Before Starting

- **Git** - [Download here](https://git-scm.com/downloads)
- **XAMPP** (Windows) or **LAMPP** (Linux) - [Download here](https://www.apachefriends.org/)
  - This gives you Apache (web server), PHP, MySQL, and phpMyAdmin
- **A code editor** - [VS Code](https://code.visualstudio.com/) is free and beginner-friendly
- **A browser** - Chrome, Firefox, or Edge

Open your terminal or command prompt and check:

```bash
git --version
```

You should see a version number. If not, install Git first.

---

## Getting Started

### 1. Fork the repository

Go to [https://github.com/yvesdylane/flytify](https://github.com/yvesdylane/flytify) and click the **Fork** button (top-right).

This creates a copy of the project under your own GitHub account. You will modify everything, so you need your own copy.

### 2. Clone your fork

```bash
git clone git@github.com:[YOUR_GITHUB_USERNAME]/flytify.git
cd flytify
```

Replace `[YOUR_GITHUB_USERNAME]` with your actual GitHub username.

### 3. Move it into your web server folder

**XAMPP (Linux):**

```bash
sudo mv flytify /opt/lampp/htdocs/
```

**XAMPP (Windows):**
Move the `flytify` folder to `C:\xampp\htdocs\` using File Explorer.

> **Why?** Apache only serves files that are inside the `htdocs` folder. If your project is anywhere else, the browser can't reach it.

### 4. Open it in your browser

Start Apache and MySQL from the XAMPP Control Panel, then visit:

```
http://localhost/flytify/
```

You should see the landing page (`index.html`).

> **Important:** Right now the pages are `.html` files. You can see them, click around, and test the design. But the form won't submit anywhere yet, and nothing saves to a database. That's intentional - you'll add those parts later.

---

## The Big Picture - How It All Fits Together

Here is what this project does, in plain English:

1. A visitor comes to your landing page (`index.html`)
2. They click "Create Your Brochure" and go to the builder (`test.html`)
3. They pick a template, fill in their info, choose colours, upload a logo
4. They click "Generate"
5. The app creates a custom brochure using their data and the template they chose
6. The brochure is displayed and they can print it or save it

**The problem:** Step 4-6 currently don't work. The HTML pages are static - they look nice but can't process data. That's where PHP and MySQL come in.

**HTML** is for *showing* content. It makes pages look good in a browser.

**CSS** is for *styling* content. It controls colours, fonts, and layout.

**JavaScript** is for *interacting* in the browser. It can update colours live, validate forms, and show previews.

**PHP** is for *processing* on the server. It receives form data, talks to the database, and creates the final brochure.

**MySQL** is for *storing* data permanently. Every brochure someone creates gets saved so you can retrieve it later.

---

## Project Files Explained

```
flytify/
├── README.md                 # ← This file. Full guide.
├── AGENTS.md                 # Instructions for AI coding tools (if you use them)
├── LICENSE                   # GPL v3 - open source license
├── .gitignore                # Files Git should ignore (.env, uploads/)
├── .env.example              # Template for environment variables
│
├── index.html                # Landing page - introduces the service
├── test.html                 # Builder page - template picker + form
├── hint.php                  # Code snippets to help you build generate.php
│
├── assets/
│   ├── css/
│   │   └── style.css         # All the styles for the site
│   ├── js/
│   │   └── script.js         # Interactive features (colour preview, etc.)
│   └── images/               # Put your images here
│
├── models/
│   ├── model1.html           # Brochure template 1 - replace with yours
│   └── model2.html           # Brochure template 2 - replace with yours
│
├── config/
│   └── schema.sql            # Database structure (incomplete - you finish it)
│
└── uploads/                  # User-uploaded logos go here (gitignored)
```

### `index.html` - Landing page

This is the first thing visitors see. It explains what the service does and shows off available templates.

**What you need to do:** Replace every `[bracketed text]` with your own content. Change the company name, the headline, the description, and the footer. When you're comfortable with PHP, rename this file to `index.php` so you can add dynamic features later (like a contact form in the footer).

### `test.html` - Builder page

This is where users pick a template and fill in their information. It contains:
- Radio buttons to select a model (template)
- Text fields for name, company, tagline, email, phone
- Colour pickers for brand colours
- A file upload for their logo

**What you need to do:**
1. Add more form fields (address, website, social media links - whatever your brochure needs)
2. Give each `<input>` a `name` attribute (PHP uses these names to read the data)
3. Wrap everything inside `<form action="generate.php" method="POST" enctype="multipart/form-data">` - currently there's no form tag
4. Change the submit button to `<button type="submit">`
5. Later, rename to `test.php` so it can process PHP

### `assets/css/style.css` - Stylesheet

Controls how everything looks. Colours, fonts, spacing, layout.

**What you need to do:** Change the colours (look for `#3B82F6` and `#1E3A5F` - these are the blues used everywhere). Change fonts if you want. Adjust spacing and sizes. Make sure it looks good on mobile too.

### `assets/js/script.js` - JavaScript

Makes the page interactive. Currently has ONE working feature: the primary colour preview updates live when you pick a colour.

**What you need to do:**
- Make the secondary colour swatch work (it's marked `// TODO`)
- Add form validation (check that required fields are filled before submitting)
- Show a preview of the uploaded logo
- Add a character counter for the tagline

### `models/model1.html` and `model2.html` - Brochure templates

These are the brochure designs. Replace them with your own HTML designs.

**Important:** Keep the `{{PLACEHOLDER}}` tags. These are markers that get replaced with the user's actual data. For example:

```html
<h1>{{COMPANY_NAME}}</h1>
<p>{{TAGLINE}}</p>
```

Available placeholders:
- `{{FULL_NAME}}` - User's name
- `{{COMPANY_NAME}}` - Their company
- `{{TAGLINE}}` - Their slogan
- `{{EMAIL}}` - Email address
- `{{PHONE}}` - Phone number
- `{{PRIMARY_COLOR}}` - Primary brand colour (hex)
- `{{SECONDARY_COLOR}}` - Secondary brand colour (hex)
- `{{LOGO_PATH}}` - Path to their uploaded logo

**To add a new template:** Copy `model1.html` to `model3.html`, replace the content with your own design, add it to the model selector in `test.html`.

### `config/schema.sql` - Database blueprint

Explains why a database is needed and provides an incomplete SQL table. Your job is to add the missing columns then import it into phpMyAdmin.

### `hint.php` - Code hints

A collection of commented-out PHP snippets. Nothing runs. When you're ready to build `generate.php`, open this file and use the snippets as a starting point.

### `.env.example` - Environment template

Contains placeholders for database connection settings. You copy it to `.env`, fill in your actual details, and PHP reads it from there.

**Why not just write the credentials directly in the code?** Because if you share your code on GitHub (and you will), everyone would see your database password. The `.env` file is listed in `.gitignore` so it never gets uploaded. Only `.env.example` (which has no real passwords) is shared.

---

## Your Tasks - Step by Step

Work through these in order. Each step builds on the previous one.

### Task 1: Customise the HTML pages

Open `index.html` and `test.html`. Replace every `[bracketed text]` with your own content. Change the company name, add real template descriptions, update the footer.

### Task 2: Personalise the styles

Open `assets/css/style.css`. Change the colours (look for `#3B82F6` and `#1E3A5F`). Try different fonts. Adjust the spacing. Make it yours.

### Task 3: Create your own brochure templates

Open `models/model1.html`. Delete everything inside and paste your own brochure design. Use the `{{PLACEHOLDER}}` tags where user data should appear. Do the same for `model2.html` with a different design.

Add your template preview images to `assets/images/` and link them in `test.html`.

### Task 4: Fix the JavaScript

Open `assets/js/script.js`. Make the secondary colour swatch work (it's marked as a TODO). Add form validation so the "Full Name" field can't be empty. Add a logo preview that shows the selected image.

### Task 5: Set up the database

1. Open the XAMPP Control Panel and start Apache + MySQL
2. Open phpMyAdmin at `http://localhost/phpmyadmin`
3. Create a new database
4. Open `config/schema.sql`, add the missing columns, then import the file into your new database

### Task 6: Set up environment variables

1. Copy `.env.example` to `.env`: `cp .env.example .env`
2. Open `.env` and fill in your database name, username, and password
3. **Never commit `.env` to Git.** Check with `git status` that it's not listed

### Task 7: Turn HTML pages into PHP

1. Rename `index.html` to `index.php`
2. Rename `test.html` to `test.php`
3. In `test.php`, wrap the form fields with `<form action="generate.php" method="POST" enctype="multipart/form-data">`
4. Change the submit button to `<button type="submit">[Generate My Brochure]</button>`
5. Give every input field a `name` attribute (e.g. `<input name="full_name">`)

**Why convert to PHP?**
- HTML files are static - they can't process form data
- PHP files can receive form submissions, connect to databases, and generate dynamic content
- The Apache web server knows to run PHP code inside `.php` files

### Task 8: Create generate.php

Using the snippets in `hint.php` as a guide:

1. Create a new file called `generate.php`
2. Add code to check if the form was submitted (`$_SERVER['REQUEST_METHOD']`)
3. Read the form data (`$_POST`, `$_FILES`)
4. Connect to the database (create `config/database.php` with a PDO connection)
5. Insert the data into the `submissions` table using a prepared statement
6. Handle the logo upload (move it to `uploads/`)
7. Load the selected template from `models/`
8. Replace `{{PLACEHOLDER}}` tags with the user's data
9. Display the finished brochure

---

## Environment Variables (.env)

The `.env` file stores settings that change depending on where the project runs:

| Variable | What it is |
|---|---|
| `DB_HOST` | Database server address (usually `localhost`) |
| `DB_NAME` | The name of your database |
| `DB_USER` | Your MySQL username (`root` for XAMPP/LAMPP) |
| `DB_PASS` | Your MySQL password (blank for XAMPP/LAMPP) |

**The golden rule:** `.env` never goes on GitHub. `.env.example` is the one you commit - it shows other people what variables they need to set, without exposing your secrets.

---

## Going Further

Once you have the basics working, try these challenges:

1. **Add a "thank you" page** - after generating, redirect to a success page instead of showing the brochure inline
2. **Let users edit their brochure** - use the submission ID to load saved data back into the form
3. **Add PDF export** - use a PHP library like Dompdf to let users download their brochure as PDF
4. **Add user accounts** - let people sign in and manage their brochures
5. **Track template popularity** - count how many times each template is used and show it on the landing page

---

## License

GNU General Public License v3.0 - see [LICENSE](LICENSE).

---

*Built as a learning scaffold for Flytify interns. Break things, fix them, learn lots.*
