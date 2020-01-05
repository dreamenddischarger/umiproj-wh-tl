Port of Witch Hunt's official Umineko translation to the [Umineko Project](https://umineko-project.org) engine.

This is currently a work in progress and not finished -- not all chapters are translated yet, and there might bugs and crashes. You can grab the [latest release](../../releases/latest) and put it in your Umineko Project folder, then select the language in the settings, if you want to help test it. Current progress is indicated below. Not that "Complete" here merely means that the translation has been completely ported. It does not guarantee the episode being bug-free.

|Episode|Status|
|-|-|
|Episode 1: Legend of the Golden Witch|Complete|
|Episode 2: Turn of the Golden Witch|Up to chapter 14|
|Episode 3: Banquet of the Golden Witch|Not started|
|Episode 4: Alliance of the Golden Witch|Not started|
|Episode 5: End of the Golden Witch|Not started|
|Episode 6: Dawn of the Golden Witch|Not started|
|Episode 7: Requiem of the Golden Witch|Not started|
|Episode 8: Twilight of the Golden Witch|Not started|

---

Notes on project structure for contributors:
- The `story` folder is what you're interested in. Anything outside of it is irrelevant to this project.
- `story/epX/en/` contains the original Umineko Project translation. Do not modify anything here.
- `story/epX/wh/` contains a copy of that translation that's being replaced with the WH translation as I progress through the project (see commits to know where I'm at)
- `story/rest-rondo.txt` and `story/rest-nocturne.txt` are an auto-generated version of the scripts. This won't run by itself and needs manual editing. The parts that are in these files haven't been touched by me yet.

Suggested workflow:
- Cut a chunk of text out of `rest-X.txt` that corresponds to a chapter (one of the story/epX/wh/umiX_X.txt files that haven't been finished yet).
- Paste that chunk into the corresponding file, replacing everything.
- Commit and push those changes. This will let other developers know you've taken a chunk and are working on it.
- Open the file you've just changed in an editor with good diff support (personally, I use VS Code).
- Remove any suspicious translations and adjust lines to fit. The line numbers between the original translation and the new one *must* match, or else the wrong lines will be "translated". You may need to split/join some of the lines in the WH translation, but try to avoid taking any liberties while doing so such as adding extra words in the joined sentence.

Automated build process:

This repository is set up to produce a pre-release on every push. If you can push to this repo, you can just wait for the build to finish after the push and download it from [here](../../releases/latest). This page is where testers should check for latest versions of the script as well.

Manual build process:
1. Install PHP somewhere on your PATH. No extra modules are required, just the default configuration is fine.
2. `cd` to the project root.
3. `mkdir out; php update-manager/update-manager.php dscript out/wh.txt . wh`
4. Check `out/wh.txt` for anything suspicious. You probably won't find anything because the script is too complicated for human consumption.
5. `php update-manager/update-manager.php script out/wh.txt "out/Witch-Hunt.file" 8`
6. Copy the generated `.file` file to the Umineko Project directory and choose "Witch-Hunt" as your language in the game settings.
