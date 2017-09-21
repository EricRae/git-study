- First-Time Git Setup

  After you installed the git on your system, you'll want to do a few things to customize you Git environment.

  You can use the tool called `git config`  that set configuration  variables,These variables can be stored in  three different places:

  1. `/etc/gitconfig` file: Contains values for every user on the system and all their repositories. And the `--system to  config `,it reads and writes from this file specifically.
  2. `~/.gitconfig`or`~/.config/git/config` file :Only to your user, you can make Git read and write to this file specifically by passing the `--global` option.
  3. `config` file in the Git directory  of whatever repository you are currently using : Specific to that single repository.

- Your Identity

  The first thing you should do when you install Git is to set your user name and email address. This is important because every Git commit uses this information , and it's immutably baked into the commits you start creating :

  ```shell
  $git config --global user.name "Eric Ray"
  $git config --global user.email ericray@gmail.com
  ```

  if you want to override this with a different name or email address for specific projects, you can run this command without the `--global` option when you're  in that project.

- Your Editor

  Now you can set you editor which you love .if not configured , Git uses your system's default editor.

  if you want to use a different editor, you can do the following:

  ```shell
  $git config -- global core.editor emacs
  ```

- Checking Your Settings

  you can use the `git config --list` command to list all the settings Git can find at that point:

  ```
  $ git config --list
  usr.name=Eric Ray
  user.email=ericray@gmail.com
  core.editor=vim
  merge.tool=vimdiff
  ...
  ```

  you can also check what Git thinks a specific key's value is by typing

  `git config <key>`:

  ```shell
  $ git config usr.name
  Eric Ray
  ```

  ​