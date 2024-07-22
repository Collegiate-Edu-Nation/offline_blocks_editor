# offline_blocks_editor
Offline blocks editor from the FTC WebUI. 

Deployed from docs/ via GitHub Pages for remote development and (eventual) convenient access to example blocks at: https://camdenboren.github.io/offline_blocks_editor/

<details>
<summary><b>Remote Development</b></summary>

All blocks-related functionality can be utilized through the deployed website: https://camdenboren.github.io/offline_blocks_editor/

Note: none of these changes are saved automatically (beyond temporary user-side cookies), so any created blocks must be downloaded and managed by the user/team if you'd like to save your work.
</details>

<details>
<summary><b>Local Development</b></summary>

git clone this repo

If you're loading the site through your browser (so it's using file URLs), simply open src/index.html, where all blocks-related functionality can be utilized (though I see errors when attempting to load example code on Firefox-based browsers).

If you're loading the site via http URLs (like Live Preview in VSCode), then open docs/index.html, where all blocks-related functionality can be utilized.

Note: these changes should be stored locally on your computer (though downloading the blocks and managing the code directly is still a good idea).
</details>

<details>
<summary><b>Workflow</b></summary>

Though the recommended development environment makes it unintuitive to version control and/or collaborate on block code, it does provide basic support for downloading, uploading, and modifying blocks.

Download: In the blocks page, check the OpModes you'd like to download and click the right-most button on the sub-menu (Download Selected OpModes) to download the .blk file.

Upload: In that same page, clicking the second button (Upload OpModes) allows you to browse and select local .blk files to be loaded into the blocks editor.

Collaborate: I'd recommend checking your team .blk files into a github repo to ensure no changes are lost. Download the files, upload them into either the remote or local development environment, save the changes, download the blocks, then commit the changes to the repo. Once the blocks are ready to be deployed to the robot, open the standard WebUI and upload the blocks.
</details>

<details>
<summary><b>Architecture</b></summary>

src/ is simply the extracted offline editor from the WebUI. Due to the conditional statements in blocks/hardware_util.js and blocks/project_util.js checking for file vs http URLs (and calling the protocols' corresponding functions), however, most functionality breaks when attempting to deploy this as a static site over http without access to the robot controller. This is resolved by commenting out all of the conditional logic and http-specific functions responsible for this functionality, forcing the use of the files even when served via http. This is the modified code found in docs/.
</details>

<details>
<summary><b>Configuration</b></summary>

Motors: 0 = frontLeft; 1 = frontRight; 2 = backLeft; 3 = backRight;  
Servos: 0 = claw; 1 = lift;  
Digital Devices: 0 = touchSensor;  
I2C: Bus 0 = colorSensor;  
USB: Webcam 1;
</details>