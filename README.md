Port of [Witch Hunt](https://witch-hunt.com)'s [official Umineko translation](https://store.steampowered.com/app/406550) to [Umineko Project](https://umineko-project.org)

Currently a work in progress and not recommended for use.

Notes on project structure for contributors:
- The `story` folder is what you're interested in. Anything outside of it is irrelevant to this project.
- `story/epX/en/` contains the original Umineko Project translation. Do not modify anything here.
- `story/epX/wh/` contains a copy of that translation that's being replaced with the WH translation as I progress through the project (see commits to know where I'm at)
- `story/rest.txt` is an auto-generated version of the script for Question Arcs. The parts that are in this file haven't been touched by me yet.

Suggested workflow:
- Cut a chunk of text out of `rest.txt` that corresponds to a chapter (one of the story/epX/wh/umiX_X.txt files that haven't been finished yet).
- Paste that chunk into the corresponding file, replacing everything.
- Commit and push those changes. This will let other developers know you've taken a chunk and are working on it.
- Open the file you've just changed in an editor with good diff support (personally, I use VS Code).
- Remove any suspicious translations and adjust lines to fit. The line numbers between the original translation and the new one *must* match, or else the wrong lines will be "translated". You may need to split/join some of the lines in the WH translation, but try to avoid taking any liberties while doing so such as adding extra words in the joined sentence.

Build process:
1. Install PHP somewhere on your PATH. No extra modules are required, just the default configuration is fine.
2. `cd` to the project root.
3. `mkdir out; php update-manager/update-manager.php dscript out/wh.txt . wh`
4. Check `out/wh.txt` for anything suspicious. You probably won't find anything because the script is too complicated for human consumption.
5. `php update-manager/update-manager.php script out/wh.txt "out/Witch-Hunt.file" 8`
6. Copy the generated `.file` file to the Umineko Project directory and choose "English (Witch Hunt)" as your language in the game settings.
