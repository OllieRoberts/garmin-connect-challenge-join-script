# Garmin Connect Challenge Auto-Join Script

This repository contains a JavaScript snippet that automates joining all available challenges on the Garmin Connect Challenge page. The script identifies **Join** buttons and simulates user clicks to save time and effort.

## How It Works
1. Finds all **Join** buttons on the Garmin Connect Challenge page using the `aria-label="Join Challenge"` attribute.
2. Loops through each button and simulates a real mouse click using `MouseEvent`.
3. Adds a short delay (1.5 seconds) between clicks to ensure smooth interaction with the page.

## Usage
1. Open the [Garmin Connect Challenges](https://connect.garmin.com/modern/challenge) page in your browser.
2. Open the browser's developer console:
   - Right-click anywhere on the page and select **Inspect**.
   - Go to the **Console** tab.
3. Copy and paste the script below into the console and press **Enter**.

## Script
```javascript
(async () => {
    // Find all 'Join' buttons by matching the aria-label attribute
    const joinButtons = Array.from(document.querySelectorAll('button[aria-label="Join Challenge"]'));

    console.log(`Found ${joinButtons.length} Join buttons to click`);

    // Loop through each button and simulate clicks
    for (let index = 0; index < joinButtons.length; index++) {
        console.log(`Clicking Join button ${index + 1} of ${joinButtons.length}`);
        
        // Dispatch a mouse click event for better interaction
        joinButtons[index].dispatchEvent(new MouseEvent('click', {
            bubbles: true,
            cancelable: true,
            view: window
        }));

        // Wait 1.5 seconds between clicks to ensure smooth interaction
        await new Promise(r => setTimeout(r, 1500));
    }

    console.log("All challenges should now be joined!");
})();
```

## Disclaimer
* This script is provided for educational purposes only and is not endorsed by Garmin. Use of this tool is entirely at your own risk.
* By using this script, you agree to take full responsibility for any actions taken with it and ensure that you comply with Garmin’s Terms of Service, Conditions, and any applicable laws or regulations.
* The creators of this repository assume no liability for any misuse, damages, or violations resulting from the use of this script.

## The Ironic Note
Sure, it’s quicker to click manually on a few challenges, but where’s the fun in that? 😉
