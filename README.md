# offline_blocks_editor

![Static Badge](https://img.shields.io/badge/FTC_SDK-11.0-mediumblue?style=for-the-badge)
![Static Badge](https://img.shields.io/badge/Platforms-Linux,_macOS,_Windows-forestgreen?style=for-the-badge)

Offline blocks editor from the FTC WebUI, deployed for painless remote development

Deployed at https://collegiate-edu-nation.github.io/offline_blocks_editor

Includes configured hardware devices and example code

Ideal for

- Collaboration
- Instruction
- Prototyping
- Homework

## Remote Development

All basic blocks functionality can be utilized through the deployed site

**None of these changes are saved automatically, so any created blocks must be downloaded and managed by the user**

## Local Development

**Must install Git before running**

- Clone this repository

  ```shell
  git clone https://github.com/collegiate-edu-nation/offline_blocks_editor.git
  ```

- If using a browser, simply open `src/index.html`
- If serving, then open `docs/index.html`

**These changes should be stored on your computer**

## Workflow

Though the recommended development environment makes it unintuitive to version control and/or collaborate on block code, it does provide basic support for downloading, uploading, and modifying blocks

### Download

- Check the OpModes you'd like to download
- Click `Download Selected OpModes` (right-most button on the sub-meu)

### Upload

- Click `Upload OpModes` (second button)
- Select desired `.blk` files

### Collaborate

I recommend using Git and GitHub to store your code regardless of whether you're using offline_blocks_editor. It's the de facto tool for developing and sharing code in teams, and the sooner students learn to use it, the better

Here's how to transition to offline_blocks_editor and Git

1. Download the `.blk` files from the WebUI on your robot
2. Upload the files into offline_blocks_editor
   - Delete the `.blk` files from your computer after uploading
3. Save changes
4. Download the `.blk` files again
5. Create a Git repository and add the `.blk` files

If any changes need to be made, simply repeat steps 3-5

Once the blocks are ready to be deployed to the robot, open the standard WebUI and upload the `.blk` files from your git repo

## Configuration

### Motors

- frontLeft
- frontRight
- backLeft
- backRight
- lift

### Servos

- clawLeft
- clawRight

### Other

- touchSensor
- distanceSensor

## Implementation

`src` is simply the extracted offline editor from the WebUI

Due to the conditional statements in `blocks/hardware_util.js` and `blocks/project_util.js` checking for file vs HTTP URLs (and calling the protocols' corresponding functions), however, most functionality breaks when attempting to deploy this as a static site over HTTP without access to the robot controller

This is resolved by commenting out all of the conditional logic and HTTP-specific functions responsible for this functionality, forcing the use of the files even when served via HTTP. This is the modified code found in `docs`
