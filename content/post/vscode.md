+++
date = '2025-01-05T12:42:08+08:00'
draft = false
title = 'vscode配置文件'
categories = '配置文件'
+++

## Workflow tips

* 在相邻的两个Tab之间切换, 可以使用`ctrl+tab`.



## settings.json

```json
{
    "window.zoomLevel": 1.1,
    "editor.fontSize": 18,
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
    "workbench.tree.indent": 35,
    
    "explorer.openEditors.visible": 1,

    "terminal.integrated.fontSize": 18,
    "terminal.integrated.lineHeight": 1.5,
    "terminal.integrated.fontFamily": "'0xProto Nerd Font'",
    "terminal.integrated.commandsToSkipShell": [
        "workbench.view.explorer",
        "workbench.action.focusLeftGroup",
        "workbench.action.focusRightGroup",
        "workbench.action.focusBelowGroup",
        "workbench.action.focusAboveGroup",
        "workbench.action.toggleZenMode",
    ],
    "zenMode.hideLineNumbers": false,
	"zenMode.centerLayout": false,
	"zenMode.showTabs": "none",
	"zenMode.fullScreen": false,

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
        { "before": ["g", "s"], "commands": ["opensshremotes.openEmptyWindow"] },
        { "before": ["<leader>", "q"], "commands": ["workbench.files.action.collapseExplorerFolders"] },
        { "before": ["<leader>", "w"], "commands": ["workbench.action.tasks.runTask"] },
        { "before": ["<leader>", "e"], "commands": ["workbench.view.explorer"] },
        { "before": ["<leader>", "a"], "commands": ["workbench.action.createTerminalEditorSide"] },
        { "before": ["<leader>", "f"], "commands": ["workbench.view.search"] },
        { "before": ["<leader>", "x"], "commands": ["workbench.action.debug.selectandstart"] },
        { "before": ["<leader>", "d"], "commands": ["workbench.debug.action.toggleRepl"] },
        { "before": ["<leader>", "p"], "commands": [
            "workbench.action.openPreviousEditorFromHistory",
            "workbench.action.quickOpenNavigateNext"
        ]},
        { "before": ["<leader>", "s"], "commands": ["workbench.action.quickOpen"] },
        { "before": ["<leader>", "m"], "commands": ["workbench.action.toggleEditorWidths"] },
        { "before": ["<leader>", "z"], "commands": ["workbench.action.toggleZenMode"] },
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

```json
[
    { "key": "ctrl+b", "command": "workbench.action.focusActiveEditorGroup" },
    { "key": "ctrl+[", "command": "workbench.action.previousEditor" },
    { "key": "ctrl+]", "command": "workbench.action.nextEditor" },
    { "key": "ctrl+h", "command": "workbench.action.focusLeftGroup" },
    { "key": "ctrl+j", "command": "workbench.action.focusBelowGroup" },
    { "key": "ctrl+k", "command": "workbench.action.focusAboveGroup" },
    { "key": "ctrl+l", "command": "workbench.action.focusRightGroup" },
    { "key": "ctrl+i", "command": "workbench.action.createTerminalEditor" },
    { "key": "ctrl+z", "command": "workbench.debug.action.toggleReplorkbench.action.toggleZenMode" },
    { "key": "ctrl+m", "command": "workbench.action.toggleEditorWidths" },
    { "key": "ctrl+t", "command": "workbench.action.tasks.runTask" },
    { "key": "ctrl+s", "command": "workbench.action.quickOpen" },
]
```



## tasks.json

```json
{
    "version": "2.0.0",
    "tasks": [
      	{
            "label": "Task A",
            "type": "shell",
            "command": "python3",
            "args": [ "main.py" ],
            "options": { "cwd": "${workspaceFolder}" }
        },
        {
            "label": "(Utils) FZF Show External File Path",
            "type": "shell",
            "command": "fd -H ${input:prompt} ${input:start_path} | fzf",
            "problemMatcher": []
        },
        {
            "label": "(Utils) FZF Open External Dir in System Explorer",
            "type": "shell",
            "command": "fd -H ${input:prompt} ${input:start_path} | fzf | xargs dirname | xargs open",
            "problemMatcher": []
        },
        {
            "label": "(Utils) FZF Open External File in Vscode",
            "type": "shell",
            "command": "fd -H ${input:prompt} ${input:start_path} | fzf | xargs code -r",
            "problemMatcher": []
        },
        {
            "label": "(Utils) FZF Open External md in Typora",
            "type": "shell",
            "command": "fd -H ${input:prompt} ${input:start_path} -e md | fzf | xargs open -a typora",
            "problemMatcher": []
        },
    ],
    "inputs": [
        {
            "id": "prompt",
            "type": "promptString",
            "description": "Input some cues about your file/dir"
        },
        {
            "id": "start_path",
            "type": "promptString",
            "description": "Input the start path for search"
        }
    ]
}

```



## launch.json

### Python

```json
{
    "version": "2.0.0",
    "configurations": [
        {
            "name": "Debug Python",
            "type": "debugpy",
            "request": "launch",
            "program": "${workspaceFolder}/main.py",
			"args": [
				"-c",
				"xxxxxx"
			],
            "console": "integratedTerminal",
			"justMyCode": true,
        },
    ]
}
```

