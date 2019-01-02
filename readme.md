# Pure

> Pretty, minimal and fast ZSH prompt, blended with personal touches

## Overview

Most prompts are cluttered, ugly and slow. I wanted something visually
pleasing that stayed out of my way. Sindre Sorhus did most of the work
with Pure, but there's no way I can leave a prompt config alone without
customizng the bajeezus out of it.

### Why?

- Shows `git` branch and whether it's dirty (with a `*`).
- Indicates when you have unpushed/unpulled `git` commits with up/down arrows. *(Check is done asynchronously!)*
- Prompt character turns red if the last command didn't exit with `0`.
- Command execution time will be displayed if it exceeds a set threshold.
- Username and host only displayed when in an SSH session.
- Shows the current path in the title and the when a process is running.
- Support VI-mode indication by reverse prompt symbol (Zsh 5.3+).
- Makes an excellent starting point for your own custom prompt. (Yes, it did!
  Thanks, Sindre!)


## Install

Requires Git 2.0.0+ and ZSH 5.2+. Older versions of ZSH are known to work, but they are **not** recommended.

1. Do one of the following:
  - Clone this repo
  - add it as a submodule, or
  - just download [`pure.zsh`](pure.zsh) and [`async.zsh`](async.zsh)

2. Symlink `pure.zsh` to somewhere in [`$fpath`](https://www.refining-linux.org/archives/46-ZSH-Gem-12-Autoloading-functions.html) with the name `prompt_pure_setup`.

3. Symlink `async.zsh` in `$fpath` with the name `async`.


#### Example

```console
$ ln -s "$PWD/pure.zsh" /usr/local/share/zsh/site-functions/prompt_pure_setup
$ ln -s "$PWD/async.zsh" /usr/local/share/zsh/site-functions/async
```
*Run `echo $fpath` to see possible locations.*

For a user-specific installation (which would not require escalated privileges), simply add a directory to `$fpath` for that user:

```sh
# .zshenv or .zshrc
fpath=( "$HOME/.zfunctions" $fpath )
```

Then install the theme there:

```console
$ ln -s "$PWD/pure.zsh" "$HOME/.zfunctions/prompt_pure_setup"
$ ln -s "$PWD/async.zsh" "$HOME/.zfunctions/async"
```


## Getting started

Initialize the prompt system (if not so already) and choose `pure`:

```sh
# .zshrc
autoload -U promptinit; promptinit
prompt pure
```


## Options

| Option                           | Description                                                                                    | Default value  |
| :------------------------------- | :--------------------------------------------------------------------------------------------- | :------------- |
| **`PURE_CMD_MAX_EXEC_TIME`**     | The max execution time of a process before its run time is shown when it exits.                | `5` seconds    |
| **`PURE_GIT_PULL=0`**            | Prevents Pure from checking whether the current Git remote has been updated.                   |                |
| **`PURE_GIT_UNTRACKED_DIRTY=0`** | Do not include untracked files in dirtiness check. Mostly useful on large repos (like WebKit). |                |
| **`PURE_GIT_DELAY_DIRTY_CHECK`** | Time in seconds to delay git dirty checking when `git status` takes > 5 seconds.               | `1800` seconds |
| **`PURE_PROMPT_SYMBOL`**         | Defines the prompt symbol.                                                                     | `❯`            |
| **`PURE_PROMPT_VICMD_SYMBOL`**   | Defines the prompt symbol used when the `vicmd` keymap is active (VI-mode).                    | `❮`            |
| **`PURE_GIT_DOWN_ARROW`**        | Defines the git down arrow symbol.                                                             | `⇣`            |
| **`PURE_GIT_UP_ARROW`**          | Defines the git up arrow symbol.                                                               | `⇡`            |

## Example

```sh
# .zshrc

autoload -U promptinit; promptinit

# optionally define some options
PURE_CMD_MAX_EXEC_TIME=10

prompt pure
```

## License

MIT © [Lonnon Foster](https://github.com/lonnon)
