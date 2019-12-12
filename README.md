# WSL
Setup guide for WSL with Debian


### Enforce LF

Most editors in the Windows environment will be able to handle LF and CRLF, but using CRLF can lead to a dirtied git repository, as files are marked changed even if the only change was the line endings. This happens quite frequently.

This can be solved by enforcing LF.

git config --global core.autocrlf input
git config --global core.eol lf

Finally, check if changes have been applied using
git config --global --edit
