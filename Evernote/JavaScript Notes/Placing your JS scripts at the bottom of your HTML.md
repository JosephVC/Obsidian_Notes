---
---
we want the whole document to load when we are trying to get an element by its ID

If you put the scripts above the given HTML element, then the script has no time to see the relevant IDs, as they load **after** the script

Here, the id **video-grid** loads before the script tag calling **script.js**

<div id\="video-grid"\>

    </div\>
    <script src\="script.js"\></script\>
