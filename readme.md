# S-System Error Pages

Custom error pages for S-System (Flight Disruption Management) platform hosted on Heroku.

## Overview

These pages are served via GitHub Pages and used by Heroku when the application is unavailable due to maintenance, high demand, or dyno crashes.

## Pages

- `index.html` - Main error page (503 Service Unavailable)

## Setup Instructions

### 1. Create GitHub Repository

```bash
# Create a new repository on GitHub named 's-system-error-pages'
# Then clone and add files:
git clone https://github.com/YOUR-USERNAME/s-system-error-pages.git
cd s-system-error-pages
# Copy index.html and README.md to this folder
git add .
git commit -m "Initial commit - S-System error pages"
git push origin main
```

### 2. Enable GitHub Pages

1. Go to your repository on GitHub
2. Navigate to **Settings** → **Pages**
3. Under "Source", select **Deploy from a branch**
4. Select **main** branch and **/ (root)** folder
5. Click **Save**
6. Wait a few minutes for the site to deploy
7. Your error page will be available at: `https://YOUR-USERNAME.github.io/s-system-error-pages/index.html`

### 3. Configure Heroku

Run these commands to configure your Heroku app to use the custom error pages:

```bash
# Replace YOUR-USERNAME with your actual GitHub username
heroku config:set ERROR_PAGE_URL=https://YOUR-USERNAME.github.io/s-system-error-pages/index.html --app YOUR-HEROKU-APP-NAME
heroku config:set MAINTENANCE_PAGE_URL=https://YOUR-USERNAME.github.io/s-system-error-pages/index.html --app YOUR-HEROKU-APP-NAME
```

**Example with actual values:**
```bash
heroku config:set ERROR_PAGE_URL=https://victor-oribamise.github.io/s-system-error-pages/index.html --app s-system
heroku config:set MAINTENANCE_PAGE_URL=https://victor-oribamise.github.io/s-system-error-pages/index.html --app s-system
```

### 4. Verify Configuration

Check that your config vars are set correctly:

```bash
heroku config --app YOUR-HEROKU-APP-NAME
```

You should see:
```
ERROR_PAGE_URL:       https://YOUR-USERNAME.github.io/s-system-error-pages/index.html
MAINTENANCE_PAGE_URL: https://YOUR-USERNAME.github.io/s-system-error-pages/index.html
```

## Testing

### Test Error Page Locally
Simply open `index.html` in your browser to preview the error page.

### Test on Heroku
You can temporarily put your app in maintenance mode to test:

```bash
# Enable maintenance mode (shows maintenance page)
heroku maintenance:on --app YOUR-HEROKU-APP-NAME

# Disable maintenance mode
heroku maintenance:off --app YOUR-HEROKU-APP-NAME
```

## Customization

### Update Dashboard URL
If your S-System dashboard URL is different, update this line in `index.html`:

```html
<a href="https://s-system.kquika.com" class="btn-primary ...">
```

### Update Contact Email
The contact email is currently set to `contact@kquika.com`. To change it, update:

```html
<a href="mailto:contact@kquika.com" ...>contact@kquika.com</a>
```

## Design Notes

The error page follows S-System's design system:
- **Primary Gradient**: Purple/Indigo (#4A56E2 → #9F7AEA)
- **Font**: System default (Arial/sans-serif)
- **Framework**: Tailwind CSS
- **Logo**: S-shaped path with airplane icon and pulse animation
- **Style**: Glass-morphism card effects

## File Structure

```
s-system-error-pages/
├── index.html      # Main 503 error page
└── README.md       # This file
```

## Support

For questions or issues, contact: contact@kquika.com

---

**S-System** - Flight Disruption Management  
© 2026 Kquika, Inc. All rights reserved.