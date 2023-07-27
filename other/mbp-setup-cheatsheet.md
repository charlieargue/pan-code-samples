# 👾 Sample "MBP Setup" Cheatsheet

```
Team 💙-ed this cheatsheet I made for improving DX and productivity
```



##### Table of Contents  

- [💻 Helpful MBP Settings](#helpful-mbp-settings)
- [📱 Apps You Might Like](#apps-you-might-like)
- [⌨️ Keyboard Shortcuts:](#keyboard-shortcuts)



Assume's you're on a MacBook, have VSCode installed already, and you will be working on CSP Micro-Frontends (MFEs).

🗣 Don't hesitate to edit this document or provide feedback!



# 💻 Helpful MBP Settings

<a name="helpful-mbp-settings"> </a>

* <u>**Finder**</u> setup:
  - show hidden files:   **`SHIFT`** + **`CMD`** +  **.**  *(period)*




# 📱 Apps You Might Like

<a name="apps-you-might-like"> </a>

### 🎽 VS Code

* **to install:** https://code.visualstudio.com/download 

* VSCode Path Setup:

  * **`SHIFT`** + **`CMD`** + **P** 
  * then type **`'path'`** and you should see:

  ``` 
  Shell Command: Install 'code' command in PATH
  ```

  * select it and press **`RETURN`**



### 👾  iTerm2   `terminal`

* **to install:** https://iterm2.com/downloads.html
* not to be confused with `iTerm` (version one)
* assumes you're using **`zsh`**, the default shell on Macs these days (instead of bash, etc.)



### 🙈 oh-my-zsh   `zsh helper`

* **to install:** https://ohmyz.sh/#install (run the `shell` script)

* allows for easy theming, aliasing, etc.

* **`~/.zshrc`** config file:

  * if you ever need to add/edit your **`PATH`** env variable, for eg. mine has:

  * ```shell
    # Adding new global NPM directory (conflict with @LOREM/ipsum)
    export PATH=/Users/lorem/.npm-global/bin:$PATH
    ```

  * you can add the following **aliases** (💡 *remember to restart your terminal session for these changes to take effect!)*:

  * ```shell
    # GENERAL
    alias ls='ls -GFlash'
    alias at='lorem-ipsum'
    alias gs='git status'
    alias gp='git pull'
    alias gd='git diff'
    alias cz='code ~/.zshrc' # 👍 allows for easy editing of this file! ⛔️
    # ⛔️ assumes you did the VSCode Path Setup (up above)
    
    # STARTING a MFE (Micro-Frontend)
    alias stg='at token stg'
    alias msw='at msw'
    alias start='npm start'
    alias astart='all ; linkat && linkaui && linkcdt ; start'
    alias amsw='all ; linkat && linkaui && linkcdt ; msw'
    # 💡 alias msw='DISABLE_PRETTIER=true DISABLE_CLEAR_CONSOLE=true at msw'
    # 💡 alias start='DISABLE_PRETTIER=true DISABLE_CLEAR_CONSOLE=true npm start'
    
    # INSTALLING / SETTING-UP a MFE
    # ------------------------------- 
    # LINUX NOTE: `;`  means run sequentially   (a ; b)  ====> so a, then when done, b
    # LINUX NOTE: `&&` means run simultaneously (x && y) ====> x and y in parallel
    # ------------------------------- 
    alias all='npm run install:all'
    alias peer='npm run install:peer'
    alias ting='all ; linkat && linkaui ; at msw' 
    alias tingv='all ; linkat && linkaui ; npm start'
    
    # CYPRESS
    alias cyp='at test-e2e'
    alias cypv='AGAINST_STG=true cyp'
    alias cyph='HEADLESS=true at test-e2e'
    
    # 🔗 LINKING:
    # ------------------------------- 
    # FYI: 'TARGET': the MFE (commands are usually run from here)
    # FYI: 'SOURCE': the centralized dev tool, lorem-ipsum (AT) or csp-dev-tools (CDT)
    # ------------------------------- 
    # run these from TARGET:
    alias linkat='npm link @lorem/lorem-ipsum' 
    alias linkaui='npm link @lorem/lorem-ui'   
    alias linkcdt='npm link @lorem/dev-tools'
    alias linke='npm link @lorem/lorem'
    # 💡 from SOURCE you would simply run:  `npm link` 
    ```



### 👓 Spectacle   `window helper`

* **to install:** https://github.com/eczarny/spectacle#basic-window-actions
* allows you to organize your windows without using a mouse
* **👍 feature:** ability to quickly MAXIMIZE a window (but NOT fullscreen) 
* 🧠 make sure to `Launch Spectacle at login` (🎥 loom, 6 seconds)
* *sadly it's no longer maintained, so you may prefer to switch to [Rectangle](https://github.com/rxhanson/Rectangle)*



### ✍️ BONUS    `markdown editors`

* for a more managed approach to working with your `.md` files
* Typora - https://typora.io/
* Obsidian - https://obsidian.md/download




# ⌨️ Keyboard Shortcuts & Commands:

💎 Feel free to add any shortcuts or commands you use personally and find helpful!

<a name="keyboard-shortcuts"> </a>

### 🌍 *General* / Universal

| **`CMD`** + **`TAB`**                             | switch between apps (use  **`SHIFT`** for reverse)           |
| ------------------------------------------------- | ------------------------------------------------------------ |
| **`CMD`** + **`SPACE`**                           | bring up <u>search</u> / spotlight                           |
| **`CMD`** + **Q**                                 | <u>quit</u> current program                                  |
| **`CMD`** + **W**                                 | <u>close</u> current tab                                     |
| **`CMD`** + **T**                                 | <u>new tab</u>                                               |
| **`SHIFT`** + **`CMD`** +  **.**  *(period)*      | show hidden files in <u>Finder</u>                           |
| **`SHIFT`** + **`CMD`** + **3**                   | takes a <u>full screenshot</u> & <u>saves it</u> as a new file on your desktop |
| **`SHIFT`** + **`CMD`** + **4**                   | takes <u>portion</u> of a screenshot <br />& <u>saves it</u> as a new file on your desktop |
| **`＾CONTROL`** + **`SHIFT`** + **`CMD`** + **3** | takes a <u>full screenshot</u> & stores it in your <u>clipboard</u> |
| **`＾CONTROL`** + **`SHIFT`** + **`CMD`** + **4** | takes <u>portion</u> of a screenshot and stores it in your <u>clipboard</u> |
| **`CMD`** + **`+`** *(plus)*                      | <u>increase</u> text/font size                               |
| **`CMD`** + **`-`** *(minus)*                     | <u>decrease</u> text/font size                               |
| **`CMD`** + **0`** *(zero)*                       | reset text/font size to default                              |
| **`SHIFT`** + **`CMD`** + **/**                   | goes to Help menu (in app menu bar)                          |



### 🎽 VS Code

| **`CMD`** + **P**                    | will let you navigate to any file or symbol by typing its name |
| ------------------------------------ | ------------------------------------------------------------ |
| **`SHIFT`** + **`CMD`** + **P**      | opens command palette ([learn more](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette)) |
| **`CMD`** + **D**                    | (Select something first), selects <u>each next</u> occurence |
| **`CMD`** +  **`SHIFT`** + **D**     | (Select something first), selects <u>all</u> occurences      |
| **`CMD`** + **.**                    | (place cursor first) Auto-Imports (can do ALL at once)       |
| **`CMD`** + **click**                | (on top of an import) Jumps to Referenced file               |
| **`SHIFT`** + **`⌥ OPTION`** + **F** | auto-formats document                                        |
| **`SHIFT`** + **`⌥ OPTION`** + **O** | auto-organizes imports (at top of document)                  |
| **`＾CONTROL`** + **W**              | switch **windows**                                           |
| **`＾CONTROL`** + **Q**              | bring up (and keep pressing to toggle) thru **sidebar**, extensions, and even sub-extension panels |



### 👓 Spectacle

| **`⌥ OPTION`**  + **`CMD`** + **F** | maximize window                                            |
| ----------------------------------- | ---------------------------------------------------------- |
| **`⌥ OPTION`** + **`CMD`** + **➡️**  | move window to the right (repeat for various widths)<br /> |



### 🚚 npm

| `npm list @lorem/lorem-ui`       | to view an installed package                 |
| ------------------------------------------- | -------------------------------------------- |
| `npm list -g @lorem/lorem-ipsum` | to view a <u>globally</u>  installed package |

