# WSL
Setup guide for WSL with Debian

## Git settings

### Enforce LF

Most editors in the Windows environment will be able to handle LF and CRLF (even notepad.exe can handle LF), but using CRLF with WSL can lead to a dirtied git repository, as files are marked changed even if the only change was the line endings. This happens quite frequently.

This can be solved by enforcing LF.

```bash

git config --global core.autocrlf input

git config --global core.eol lf

```
Finally, check if changes have been applied using
git config --global --edit

### Ignore file permission changes

Some programs, when saving changes back to a file, don't honour the original file permissions, or simply delete and rewrite files. These files will have the equivalent of Windows file permissions, e.g. 755. If you work with developers that don't use Windows, you do not want to push back files with new permissions of 755.

Instead, set git to ignore all file permission changes and use the original permission instead.

```bash
git config --global core.filemode false
```

Please note you will need to take extra steps now if you want to explicitely change file mode permissions. You can do this like so:

git update-index --chmod=(+|-)x <path>
  

❗ Be sure to check inside the hidden .git folder in each repository. In most cases a file named config inside it will have set filemode = true, which overwrites your global settings.
