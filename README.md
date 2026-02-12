# YouTube Subscriptions List View

**YouTube Subscriptions List View** is a Chrome Extension (Manifest V3) that forces the YouTube Subscriptions and Home feeds into a classic, readable **List View** layout.

Modern YouTube forces a "Rich Grid" layout that hides video descriptions and truncates metadata. This extension restores the vertical list format, fetches the missing video descriptions, and provides a customizable UI to adjust the layout to your preference.

## 🚀 Features

* **Force List View:** Converts the multi-column grid into a single-column list layout on both the **Subscriptions** and **Home** feeds.
* **Smart View Toggles:** Injects **Grid** and **List** icon buttons directly onto the YouTube page, allowing you to switch layouts instantly. The extension remembers your preference separately for the Home and Subscriptions feeds.
* **Video Descriptions:** Automatically fetches and displays the video description (short snippet) for every video.
    * **Link Highlighting:** Detects URLs in descriptions and makes them clickable (customizable via settings).
* **Clean Interface:** Automatically removes **Ad** slots from the feed for a clutter-free experience.
* **Watch Later Shortcut:** Restores the missing "Watch Later" button to the sidebar if it's not present.
* **Customizable Layout:** A popup menu allows you to adjust:
    * **Container Width:** Control how wide the list is on your screen (50% - 100%).
    * **Thumbnail Size:** Resize video thumbnails (150px - 400px).
    * **Typography:** Adjust the font size for Video Titles and Metadata/Descriptions.
    * **Notify Button Width:** Adjust the spacing for the Subscribe/Notification button area.
* **Live Preview:** Adjustments made in the popup are reflected instantly on the active tab.

## 📂 File Structure

* `manifest.json` - Extension configuration (MV3).
* `content.js` - Main logic for DOM manipulation, fetching descriptions, injecting toggle buttons, and removing ads.
* `styles.css` - CSS overrides to force the grid into a list and apply user settings.
* `popup.html` & `popup.js` - The settings interface for customizing the view.

## 🛠️ Installation

Since this is a developer build, you can install it via "Load Unpacked":

1.  **Download** the source files into a folder named `youtube-list-view`.
    * Ensure `manifest.json`, `content.js`, `styles.css`, `popup.html`, and `popup.js` are all in the root of this folder.
2.  Open Google Chrome and navigate to `chrome://extensions/`.
3.  Enable **Developer mode** using the toggle switch in the top right corner.
4.  Click the **Load unpacked** button.
5.  Select the `youtube-list-view` folder you created in Step 1.
6.  The extension is now active! Go to YouTube to see the changes.

## ⚙️ Usage

1.  Navigate to [YouTube.com](https://www.youtube.com) or your Subscriptions feed.
2.  **To switch views:** Look for the **Grid/List icons** (near the "Manage" button on Subscriptions or the Filter Chips on Home) to toggle the layout instantly.
3.  **To customize the look:**
    * Click the extension icon in the Chrome toolbar.
    * Use the **sliders** to adjust width, thumbnail size, font sizes, and notify button width.
    * Toggle **Highlight Links** to colorize URLs in descriptions.
    * Changes apply immediately.
    * Click **Reset to Defaults** to revert to the original optimized settings.

## 🔧 Technical Notes

* **Permissions:**
    * `storage`: Used to save UI preferences and View Mode states (Grid/List) per feed.
    * `host_permissions` (`https://www.youtube.com/*`): Required to inject the content script and styles into YouTube.
* **Performance:**
    * The extension uses a `MutationObserver` to detect when YouTube loads new videos (infinite scroll) and applies styles dynamically.
    * Video descriptions are fetched via individual `fetch()` requests to the video URL to parse the meta description tag, with caching to prevent duplicate requests.
    * Includes logic to handle YouTube's Single Page Application (SPA) navigation and layout reflows.

## 📈 Star History

[![Star History Chart](https://api.star-history.com/svg?repos=engin0223/Youtube-List-View-Extension&type=Date)](https://star-history.com/#engin0223/Youtube-List-View-Extension&Date)
