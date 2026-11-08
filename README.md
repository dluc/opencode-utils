# opencode-utils

Small utilities for using OpenCode on your own machines.

## OpenCode launcher

OpenCode Desktop can place versioned executables under
`~/.opencode/desktop-ssh/` on an SSH host. The `opencode` launcher finds the
highest available version there and runs it, passing your arguments through
unchanged. When a newer version appears, the next invocation picks it up.

Use it when you want to run `opencode` in a shell on that host without choosing
a versioned path yourself. It does not install OpenCode or remove old versions.

### Install

You need a POSIX shell and GNU `find` and `sort` (normally available on Linux),
and at least one executable in the Desktop SSH directory.

```sh
git clone https://github.com/dluc/opencode-utils.git
cd opencode-utils
mkdir -p ~/bin
install -m 755 opencode ~/bin/opencode
```

The install command replaces an existing `~/bin/opencode`. Make sure `~/bin` is
on your `PATH` and comes before any other `opencode` you want this to replace.
Then run:

```sh
opencode --version
```

If the directory or an executable is missing, the launcher reports an error
and exits. Otherwise, it returns the selected OpenCode process's exit status.

## License

MIT. See [LICENSE](LICENSE).
