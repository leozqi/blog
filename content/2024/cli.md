+++
title="Command-line tips and tricks"
date=2024-03-11
+++

Almost every Linux CLI tool that requires you to edit a file will consult the `EDITOR` environment variable to spawn the editor you prefer. So, if you want to use `nano` instead of `vim`, simply set it as your default editor in your `.bashrc` or `.zshrc`:

`export EDITOR=nano`

- Monospace Mentor @floss.social
