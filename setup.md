# Kunal Pathak's Presentations

This document explains how to setup and manage presentations built with [Reveal.js](https://revealjs.com/) and [Remark.js](https://remarkjs.com/), whether you are working within this repository or starting a new one inspired by it.

## Links to Presentations

- [Sample Reveal.js (Scroll View)](https://presentations.kunal-pathak.com/templates/revealjs/200-reveal_scroll.html)
- [Sample Reveal.js (External Markdown)](https://presentations.kunal-pathak.com/templates/revealjs/100-reveal-external_markdown.html)
- [Sample Remark.js](https://presentations.kunal-pathak.com/templates/remarkjs/100-remark.html)

---

## A. Starting afreash with a new repository

Follow these steps if you want to create a new repository for your presentations from scratch, using this repository as a reference.
Create local repository and add the submodule.

- `git submodule add https://github.com/hakimel/reveal.js reveal.js`

## B. Setting Up THIS Cloned Repository (`kanad13/kanad13`)

Follow these steps if you have cloned _this specific repository_ (`kanad13/kanad13`) and want to work with its existing structure and content.

### 1. Clone This Repository and Initialize Submodules

To get a copy of this repository and its submodules (like Reveal.js):

**Option 1: Clone with submodules (recommended)**

```bash
git clone --recurse-submodules https://github.com/hakimel/reveal.js
cd kanad13
```

**Option 2: Clone first, then initialize submodules**

```bash
git clone https://github.com/kanad13/kanad13.git
cd kanad13
git submodule update --init --recursive
```

### 2. (Optional) Install Reveal.js Dependencies

The Reveal.js submodule has its own `package.json`. If you plan to use its build tools or ensure all its development dependencies are met:

```bash
cd reveal.js
npm install
cd ..
```

_This is typically done once after cloning/initializing the submodule, or if Reveal.js itself has updates to its dependencies._

---

## B. Working with Presentations WITHIN This Repository

### Viewing Presentations Locally

Presentations are HTML files. Open the respective `.html` file (e.g., `templates/revealjs/200-reveal_scroll.html` or `templates/remarkjs/100-remark.html`) directly in your web browser to view it.

### Creating New Presentations

All presentation decks are in the `./templates/` directory, organized by framework (`revealjs` or `remarkjs`).

#### Reveal.js

- **Location:** `./templates/revealjs/`
- **To Create:**
  1.  Copy an existing Reveal.js HTML file (e.g., `100-reveal-external_markdown.html` for external Markdown, or `200-reveal_scroll.html` for inline Markdown) or create a new one.
  2.  If using external Markdown, create a corresponding `.md` file (like `101-reveal-external_markdown.md`).
  3.  Update paths in your HTML to `../../reveal.js/...` for core files and `../../assets/...` for your custom assets.
  4.  Edit your HTML or Markdown content.

#### Remark.js

- **Location:** `./templates/remarkjs/`
- **To Create:**
  1.  Copy `100-remark.html` and its associated `.md` file (e.g., `101-remark.md`).
  2.  Rename them and update the `sourceUrl` in the HTML file to point to your new Markdown file.
  3.  Edit your Markdown slide content.

### Shared Assets

- **Custom CSS:**
  - `assets/css/revealjs-white.css` (for Reveal.js)
  - `assets/css/remarkjs-github.css` (for Remark.js)
- **Images:** `assets/images/`
  - Please add your own images to this directory and update the paths in the Markdown/HTML.
- **Fonts:** `assets/fonts/`
  - Google Fonts (Montserrat) are used by default and linked in the HTML templates. The `assets/fonts/` directory is available if you wish to self-host font files and update the CSS accordingly.

---

## C. Creating a NEW, Separate Presentation Repository (Inspired by this one)

If you want to start a completely new repository for presentations from scratch but use a similar structure with Reveal.js as a submodule:

1.  **Create and Clone Your New Repository:**
    Create a new repository on GitHub (e.g., `my-new-presentations-repo`).
    Then clone it:

    ```bash
    git clone https://github.com/your-username/my-new-presentations-repo.git
    cd my-new-presentations-repo
    ```

2.  **Add Reveal.js as a Submodule to Your New Repo:**
    You can use your fork or the official Reveal.js repository.

    ```bash
    git submodule add https://github.com/hakimel/reveal.js.git reveal.js
    ```

3.  **Commit the Submodule Addition:**

    ```bash
    git add .gitmodules reveal.js
    git commit -m "Add reveal.js submodule"
    ```

4.  **(Optional) Install Reveal.js Dependencies in the New Repo:**

    ```bash
    cd reveal.js
    npm install
    cd ..
    ```

5.  **Structure Your New Repository:**
    You can now copy HTML templates (like those in `templates/revealjs/` from _this_ `kanad13/presentations` repository), CSS (from `assets/css/`), and adopt a similar directory structure (`assets/`, `templates/`) in your _new_ repository as a starting point. Remember to adjust paths in your copied HTML files to point correctly to the `reveal.js` submodule and your assets within your new repository.

---

## D. Deployment

### Deployment to GitHub Pages

1.  Push your repository to GitHub.
2.  In GitHub repository settings, go to "Pages".
3.  Configure the source to be your main branch and the `/ (root)` folder.
4.  Access presentations via `https://kanad13.github.io/kanad13/<your-presentation-path>`. (If using a custom domain, see below).

### Configuring Custom Domain

Here's a detailed guide on how to set up a custom subdomain like `presentations.kunal-pathak.com` for your GitHub Pages site, using Cloudflare for DNS management. (This example assumes the custom domain is for _this_ `kanad13/presentations` repository).

**Step 1: Configure the Custom Subdomain in Your GitHub Repository**

1.  **Go to your GitHub repository:** Navigate to the repository that hosts your presentations (e.g., `kanad13/kanad13`).
2.  **Enter Your Custom Subdomain:**
    - Under the "Custom domain" section in the repository's Settings --> Pages, type in the full subdomain you want to use. For example, `presentations.kunal-pathak.com`.
    - Click **Save**.
3.  **CNAME File Creation:**
    - GitHub will automatically create a commit that adds a `CNAME` file to the root of your publishing source (your main branch's root). This file will contain your custom subdomain (e.g., `presentations.kunal-pathak.com`).

**Step 2: Add a CNAME Record in Your Cloudflare DNS Settings**

1.  **Log in to Cloudflare:** Go to the Cloudflare dashboard and log in to your account.
2.  **Select Your Domain:** Click on your domain `kunal-pathak.com`.
3.  **Navigate to DNS Settings:** In the Cloudflare dashboard for your domain, click on the "DNS" icon in the navigation menu.
4.  **Add a New CNAME Record:**
    - Click the "**+ Add record**" button.
    - **Type:** Select `CNAME` from the dropdown list.
    - **Name:** Enter your desired subdomain prefix. In this case, it would be `presentations`. Cloudflare will automatically append `kunal-pathak.com`.
    - **Target:** Enter your default GitHub Pages domain, which is `kanad13.github.io`. **Do not include your repository name here.** The CNAME record should always point to `kanad13.github.io`.
    - **Proxy status:** Keep this record "Proxied" (orange cloud) for Cloudflare benefits, or "DNS only" (grey cloud) for direct GitHub Pages handling.
    - **TTL (Time To Live):** You can generally leave this at "Auto".
    - Click **Save**.

**Step 3: Verify and Wait for Propagation**

1.  **Check GitHub Repository Settings:** Go back to your GitHub repository's "Pages" settings. After a few minutes, GitHub will try to verify your custom domain.
2.  **Wait for DNS Propagation:** DNS changes can take some time to propagate.
3.  **Check for HTTPS:** Once GitHub has successfully verified your custom domain, it will begin provisioning an SSL/TLS certificate for HTTPS. Ensure "Enforce HTTPS" is checked in GitHub Pages settings.

**Step 4: Test Your Custom Subdomain**

Once DNS has propagated and GitHub has provisioned the HTTPS certificate, you should be able to access your GitHub Pages site at `https://presentations.kunal-pathak.com`.
