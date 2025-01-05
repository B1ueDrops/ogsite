+++
date = '2025-01-05T12:42:08+08:00'
draft = false
title = 'vscode配置文件'
categories = '配置文件'
+++


## settings.json

```json
{
    "editor.fontSize": 20,
    "editor.fontFamily": "consolas",
    "editor.minimap.enabled": false, // Disable minimap
    "editor.wordWrap": "on", // when a line is two long, wrap it.
    "editor.guides.bracketPairs": true, // use line to connect brackets
    "editor.detectIndentation": false, // force vscode to ignore current file identation

    "files.simpleDialog.enable": true, // when open folder, use vscode dialog
    "files.autoSave": "afterDelay", // Set file auto save
    "files.autoSaveDelay": 500, // After 0.5s file save
    "files.autoGuessEncoding": true, // Open file in a proper encoding

    "search.defaultViewMode": "tree", // Search view default as dir tree, use ctrl+shift+f

    "workbench.colorTheme": "Shades of Purple (Super Dark)",
    "workbench.iconTheme": "material-icon-theme",
    "workbench.productIconTheme": "developer-icons",

    "terminal.integrated.fontSize": 18,
    "terminal.integrated.lineHeight": 1.5,
    "terminal.integrated.fontFamily": "'0xProto Nerd Font'",
    "terminal.integrated.commandsToSkipShell": [
        "workbench.view.explorer",
        "workbench.action.focusLeftGroup",
        "workbench.action.focusRightGroup",
        "workbench.action.focusBelowGroup",
        "workbench.action.focusAboveGroup",
    ],

    "vim.hlsearch": true,
    "vim.incsearch": true,
    "vim.leader": "<space>",
    "vim.highlightedyank.enable": true,
    "vim.normalModeKeyBindings": [
        { "before": ["J"], "after": ["6", "j"] },
        { "before": ["K"], "after": ["6", "k"] },
        { "before": ["H"], "after": ["6", "h"] },
        { "before": ["L"], "after": ["6", "l"] },
        { "before": ["W"], "after": ["$"] },
        { "before": ["B"], "after": ["^"] },
        { "before": ["g", "h"], "commands": ["editor.action.showHover"] },
        { "before": ["g", "s"], "commands": ["editor.action.indentationToSpaces"] },
        { "before": ["<leader>", "a"], "commands": ["workbench.action.createTerminalEditorSide"] },
        { "before": ["<leader>", "e"], "commands": ["workbench.view.explorer"] },
        { "before": ["<leader>", "t"], "commands": ["workbench.action.tasks.runTask"] },
        { "before": ["<leader>", "f"], "commands": ["workbench.view.search"] },
        { "before": ["<leader>", "x"], "commands": ["workbench.action.debug.selectandstart"] },
        { "before": ["<leader>", "d"], "commands": ["workbench.debug.action.toggleRepl"] },
        { "before": ["<leader>", "s"], "commands": ["opensshremotes.openEmptyWindow"] },
        { "before": ["<leader>", "c"], "commands": ["marscode.chat"] },
        { "before": ["<leader>", "o"], "commands": ["workbench.action.files.openFile"] },
    ],
    "vim.visualModeKeyBindings": [
        { "before": ["K"], "after": ["6", "k"] },
        { "before": ["H"], "after": ["6", "h"] },
        { "before": ["J"], "after": ["6", "j"] },
        { "before": ["L"], "after": ["6", "l"] },
        { "before": ["W"], "after": ["$", "h"] },
        { "before": ["B"], "after": ["^"] },
        { "before": [">"], "commands": ["editor.action.indentLines"] },
        { "before": ["<"], "commands": ["editor.action.outdentLines"] },
    ],
}
```



## keybindings.json



## tasks.json



## launch.json

