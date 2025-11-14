# Report Generator - Pure Frontend Application

A pure frontend application for generating training and cancellation reports. Course data is managed through YAML files, and changes are automatically reflected in the frontend.

## Quick Start

```bash
# 1. Install dependencies
npm install

# 2. Build Tailwind CSS for production
npm run build

# 3. Serve the application (choose one method)
python -m http.server 8000
# OR
npx http-server
# OR
php -S localhost:8000

# 4. Open http://localhost:8000 in your browser
```

## Features

- **Pure Frontend**: No backend required - works with static file serving
- **YAML-Based Course Management**: Course data stored in YAML files
- **Dynamic Loading**: Automatically loads courses from YAML files
- **Training Reports**: Generate formatted training reports with course details
- **Cancellation Reports**: Generate batch cancellation notices
- **WhatsApp Integration**: Share generated messages directly via WhatsApp
- **Responsive Design**: Works on all screen sizes

## Project Structure

```
message-generator/
├── index.html              # Main HTML file
├── app.js                  # JavaScript application logic
├── data/
│   └── courses/
│       ├── manifest.json   # List of all course YAML files
│       ├── cloud-devops-engineering-course.yaml
│       ├── ai-powered-full-stack-course.yaml
│       └── data-science-analytics-course.yaml
└── assets/
    └── favicon.svg         # Application favicon
```

## How It Works

1. **Course Loading**: On page load, the application fetches `data/courses/manifest.json` to get a list of all YAML course files.

2. **YAML Parsing**: Each YAML file listed in the manifest is fetched and parsed using the `js-yaml` library (loaded via CDN).

3. **Dynamic Updates**: When you add, edit, or delete YAML files in the `data/courses/` folder and update `manifest.json`, click the refresh button (🔄) to reload courses without a full page refresh.

## Adding or Editing Courses

1. **Add a new course**: 
   - Create a new YAML file in `data/courses/` following the existing format
   - Add the filename to `data/courses/manifest.json` in the `courses` array

2. **Edit an existing course**:
   - Edit the corresponding YAML file in `data/courses/`
   - Click the refresh button (🔄) in the header to reload courses

3. **Remove a course**:
   - Delete the YAML file from `data/courses/`
   - Remove the filename from `data/courses/manifest.json`
   - Click the refresh button (🔄) to update

## YAML Course File Format

Each course YAML file should follow this structure:

```yaml
name: Course Name
topics:
  - name: Subject Name
    main_topics:
      - name: Module/Day Name
        subtopics:
          - Subtopic 1
          - Subtopic 2
          - ...
```

## Running the Application

**Important**: Before running, make sure you've built the Tailwind CSS file:
```bash
npm install
npm run build
```

Then open `index.html` in a web browser. For best results, use a local web server:

```bash
# Using Python 3
python -m http.server 8000

# Using Node.js (http-server)
npx http-server

# Using PHP
php -S localhost:8000
```

Then navigate to `http://localhost:8000` in your browser.

## Installation & Build

### For Production Use

1. **Install dependencies:**
   ```bash
   npm install
   ```

2. **Build Tailwind CSS:**
   ```bash
   npm run build
   ```
   This generates `assets/tailwind.css` with only the CSS classes you actually use (optimized for production).

3. **For development with auto-rebuild:**
   ```bash
   npm run watch:css
   ```
   This watches for changes and rebuilds CSS automatically.

### Dependencies

- **Tailwind CSS**: Built locally for production (no CDN)
- **js-yaml**: Loaded via CDN for YAML parsing

**Note**: The built CSS file (`assets/tailwind.css`) is required for the application to work. Make sure to run `npm run build` before deploying.

## Browser Support

Works in all modern browsers that support:
- ES6 JavaScript
- Fetch API
- Local Storage
- Clipboard API

## Notes

- Course files **must** be in YAML format (`.yaml` extension)
- The `manifest.json` file must be kept up-to-date when adding or removing course files
- Changes to YAML files require clicking the refresh button (🔄) or reloading the page to be reflected

## Troubleshooting

### Courses Not Loading

- **Check browser console**: Open Developer Tools (F12) and check for error messages
- **Verify manifest.json**: Ensure `manifest.json` contains a valid `courses` array with correct filenames
- **Check YAML syntax**: Validate YAML files for proper formatting (each course must have `name` and `topics` fields)
- **Network issues**: Ensure you're running the app via a web server (not file:// protocol) to avoid CORS errors
- **Refresh courses**: Click the refresh button (🔄) in the header to reload courses

### Form Validation Errors

- **Red borders**: Fields with validation errors will show red borders
- **Error messages**: Check below each field for specific error messages
- **Required fields**: All fields marked with * are required

### WhatsApp Integration Issues

- **Browser permissions**: Some browsers may require permission to open external links
- **Pop-up blockers**: Ensure pop-up blockers allow WhatsApp links
- **No message generated**: Generate a message first before using WhatsApp button

### General Issues

- **Page not loading**: Ensure all files are in the correct directory structure
- **Styling issues**: Check internet connection (Tailwind CSS is loaded from CDN)
- **JavaScript errors**: Check browser console for detailed error messages

