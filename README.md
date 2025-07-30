Advanced File Renamer PWA
A Progressive Web App (PWA) for batch renaming files with 12 flexible renaming modes, designed to match the functionality of webrename.com. Features live preview of renamed files as options are selected, iOS compatibility, and offline support via a service worker. Users can upload files, apply renaming rules, and download renamed files as a ZIP.
Features

12 Renaming Modes: Sorting, File Extension, Case, Order, Replace, Insert, Cut, Random, Remove, List, Customize, Regular Expressions.
Live Preview: File names update instantly in the preview list when options are selected or inputs are changed.
iOS Compatibility: Installable as a PWA with full-screen support and responsive design.
Offline Support: Service worker enables offline functionality (requires initial load online).
Cross-Platform: Works on any modern browser (Chrome, Safari, Firefox, Edge).

Setup Instructions
Prerequisites

A modern web browser (e.g., Chrome, Safari, Firefox, Edge).
Node.js and npm (for local development and CSS compilation).
An HTTPS server for PWA functionality (e.g., Netlify, Vercel, or a local server with HTTPS).

Project Structure
Ensure the following files are in your project directory:

index.html: Main application file with UI and logic.
styles.css: Compiled Tailwind CSS styles.
input.css: Source CSS for Tailwind compilation.
tailwind.config.js: Tailwind configuration.
manifest.json: PWA manifest for installability.
sw.js: Service worker for offline support.
apple-touch-icon.png: 180x180 PNG icon for iOS home screen.

Installation

Clone or Download the Project:
Download the project files or clone the repository.


Compile Tailwind CSS:
Ensure tailwind.config.js contains:/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ['./index.html'],
  theme: { extend: {} },
  plugins: []
}


Run:npx tailwindcss -i ./input.css -o ./styles.css --minify


This generates styles.css from input.css.


Host the Application:
Deploy to an HTTPS server (e.g., Netlify, Vercel) for PWA support.
For local testing, use a tool like http-server with HTTPS:npm install -g http-server
http-server -S -C cert.pem -K key.pem

(Requires generating cert.pem and key.pem for HTTPS.)


Install as PWA on iOS:
Open the URL in Safari.
Tap the Share icon > Add to Home Screen.
Launch from the Home Screen for standalone mode.


Optional: Native iOS App:
Install Capacitor: npm install @capacitor/core @capacitor/cli @capacitor/ios.
Initialize: npx cap init, then npx cap add ios, npx cap copy, npx cap open ios.
Add native features (e.g., Filesystem plugin) for App Store submission.
Build and distribute via Xcode on a Mac.



Usage Instructions
Accessing the App

Open the app in a browser or install it as a PWA for a native-like experience.
On iOS, ensure the app is scrollable and displays correctly at 100% zoom in standalone mode.

Uploading Files

Click the Upload Files button or drag and drop files into the input area.
Files appear in the preview list below, showing original and new names (initially identical).

Renaming Files
The app offers 12 renaming modes, each with specific options. Select a mode by checking an option (e.g., a checkbox) or entering text. The preview list updates instantly to reflect changes. Only one option per mode can be active at a time.
1. Sorting

Options: Natural Sorting, File Name Order, Reverse File Name Order, Modification Time Order, Reverse Modification Time Order, Random Order, Reverse Sorting.
Usage: Check one sorting method. The file list reorders immediately.
Example: Check "Natural Sorting" to sort files alphanumerically (e.g., file1.txt, file2.txt).

2. File Extension

Options:
Convert to Uppercase (e.g., .txt → .TXT).
Convert to Lowercase (e.g., .TXT → .txt).
Change to: Enter a custom extension (e.g., jpg).


Usage: Check an option and (for custom) enter an extension. Preview updates instantly.
Example: Check "Convert to Uppercase" to change image.jpg to image.JPG.

3. Case

Options: Uppercase, Lowercase, Title Case, Sentence Case.
Settings: Ignore File Extensions (checked by default).
Usage: Check one case mode. Preview updates to show renamed files.
Example: Check "Title Case" to change my_file.txt to My_File.txt.

4. Order

Options:
Number Template: Enter a template (e.g., #, {self}_#, file-#) or select from dropdown (#, {self}_#, #_{self}, file-#, img-#).
Starting Number: Set the starting number (e.g., 1).
Number Increment: Set the increment (e.g., 1).
Number of Digits: Set the digit padding (e.g., 2 for 01).


Usage: Adjust template and numbers. Preview shows sequential names.
Example: Set template to file-# and digits to 2 to rename image.jpg to file-01.jpg.

5. Replace

Options:
Searched Text: Enter text to replace.
Replaced Text: Enter replacement text.
Replacement Scope: All, First, Last One, Specify Range (with Start/End inputs).
Settings: Ignore File Extensions (default), Ignore Case.


Usage: Enter search/replace text, check a scope, and adjust settings. Click "Add Another Rule" for multiple replacements. Preview updates instantly.
Example: Replace "img" with "photo" to change img001.jpg to photo001.jpg.

6. Insert

Options:
Insert Text: Enter text to insert.
Extraction Type: Before Filename, After Filename, After Specified Position, After Specified Text.
Settings: Ignore File Extensions (default).


Usage: Enter text, check an insertion type, and specify position/text if needed. Preview updates instantly.
Example: Insert "new_" before filename to change file.txt to new_file.txt.

7. Cut

Options:
Extraction Type: After Specified Position, After Specified Text.
Trim from Nth Character: Set start position.
Trim Length: Set extraction length (negative for end-based).
Settings: Ignore File Extensions (default).


Usage: Check a type, set position/text and length. Preview updates instantly.
Example: Cut after position 2 with length 3 to change abcdef.txt to bcd.txt.

8. Random

Options:
Character Sets: Lowercase, Uppercase, Numbers, Special Symbols, Custom (with default values).
Name Length: Set length of random string.
Insert Position: Replace Filename, Before Filename, After Filename, After Specified Position, After Specified Text.


Usage: Adjust character sets, length, and position. Preview shows random names.
Note: File names are case-insensitive on Windows; prefer lowercase.
Example: Replace with 8 lowercase letters to change file.txt to abcdefgh.txt.

9. Remove

Options:
Character Sets: Lowercase, Uppercase, Numbers, Chinese Characters, Special Symbols, Custom (with defaults).
Settings: Remove All Except Selected, Ignore File Extensions (default).


Usage: Specify characters to remove or keep. Preview updates instantly.
Example: Remove numbers to change file123.txt to file.txt.

10. List

Options:
Name List: Paste a list of names (one per line).
Insert Position: Replace Filename, Before Filename, After Filename, After Specified Position, After Specified Text.
Settings: Ignore File Extensions (default).


Usage: Paste names, check a position. Preview updates instantly.
Example: Paste newname to rename file.txt to newname.txt.

11. Customize

Options:
Name List: Paste a translation table ([Original Name] [Delimiter] [New Name]).
Delimiter: Set delimiter (default: Tab).


Usage: Paste table, set delimiter. Preview updates instantly.
Example: Paste file.txt new_file.txt to rename file.txt to new_file.txt.

12. Regular Expressions

Options:
Search Rules: Enter regex pattern (e.g., txt\d{1}).
Replacement Rules: Enter replacement (e.g., file-$1).
Settings: Ignore File Extensions (default), Ignore Case, Global Match (default).


Usage: Enter regex and replacement. Preview updates instantly.
Example: Use txt(\d{1}) and file-$1 to change txt1.jpg to file-1.jpg.

Downloading Renamed Files

After configuring a renaming mode, the preview list shows the new names.
Click Rename & Download to generate a ZIP file (renamed_files.zip) with the renamed files, using the currently selected mode (first checked option).

Notes

Single Mode Selection: Only one option per mode can be active (checking a new option unchecks others in the same group).
Live Preview: Changes to checkboxes, text inputs, or dropdowns instantly update the preview list.
Error Handling: Invalid regex patterns trigger an alert. Ensure the number of names in List mode matches the number of files for best results.
iOS Considerations: The app is optimized for iOS with a responsive design and PWA support. Test in Safari’s standalone mode.

Troubleshooting

PWA Not Installing: Ensure the site is served over HTTPS and manifest.json is accessible.
Preview Not Updating: Check that at least one option is selected or text is entered. Clear browser cache if issues persist.
Large File Sets: Live preview may slow down with many files. Consider fewer files or contact the developer for optimization.
App Store Submission: For a native iOS app, add Capacitor plugins (e.g., Filesystem, Notifications) to meet Apple’s guidelines.

Developer Notes

Dependencies: JSZip (3.10.1) and FileSaver.js (2.0.5) are included via CDN. Tailwind CSS requires Node.js for compilation.
Extending Features:
Add debouncing to input events for performance with large file sets.
Implement collapsible sections using Alpine.js or Tailwind’s data-* attributes.
Add increment/decrement buttons for number inputs with JavaScript.


Contributing: Submit pull requests or issues to the repository (if hosted).

License
MIT License. Use and modify freely, with no warranty provided.

Last Updated: July 30, 2025
