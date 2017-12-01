---
title: "Vscode With Git Bash"
date: 2017-12-01T20:54:58+08:00
draft: false
---

## 打开VSCode，点击 文件 \ 首选项 \ 用户设置，这是我的配置。
```
{
    "editor.tabSize": 2,
    
    "files.autoSave":"off",
    "eslint.validate": [
       "javascript",
       "javascriptreact",
       "html",
       { "language": "vue", "autoFix": true }
     ],
     "eslint.options": {
        "plugins": ["html"]
    },
    "window.menuBarVisibility": "default",
    "terminal.integrated.shell.windows": "C:\\Program Files\\Git\\bin\\bash.exe"
  }
  ```