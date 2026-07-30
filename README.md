# Codex Update Wrapper

  A lightweight Bash wrapper for the Codex CLI that checks npm for updates, offers to install the latest version, and then launches Codex.

  ## Features

  - Checks for new `@openai/codex` releases at startup
  - Displays the installed and available versions
  - Prompts before installing an update
  - Skips update checks in non-interactive sessions
  - Continues with the installed version if an update fails
  - Supports custom Codex installation paths
  - Can disable update checks when needed

  ## Requirements

  - Linux or WSL
  - Bash
  - Node.js and npm
  - GNU `timeout` and `sort`
  - Codex installed globally through npm

  Install Codex with:

  ```bash
  npm install -g @openai/codex
  ```

  By default, the wrapper expects the official Codex executable at:

  ```text
  ~/.local/share/npm-global/bin/codex
  ```

  ## Installation

  Clone the repository:

  ```bash
  git clone https://github.com/DevilsNerve/codex-update-wrapper.git
  cd codex-update-wrapper
  ```

  Install the wrapper:

  ```bash
  mkdir -p "$HOME/.local/bin"
  install -m 755 codex "$HOME/.local/bin/codex"
  ```

  Make sure `~/.local/bin` appears before the npm global binary directory in your `PATH`.

  Verify the active command:

  ```bash
  type -a codex
  ```

  The first result should be:

  ```text
  /home/YOUR_USERNAME/.local/bin/codex
  ```

  ## Usage

  Launch Codex normally:

  ```bash
  codex
  ```

  When an update is available, the wrapper displays:

  ```text
  Codex update available: 0.145.0 -> 0.146.0
  Update now with npm install -g @openai/codex@latest? [Y/n]
  ```

  Press Enter or type `y` to update. Type `n` to launch the currently installed version.

  All command-line arguments are forwarded to the official Codex executable:

  ```bash
  codex --help
  codex --version
  ```

  ## Configuration

  ### Skip the update prompt

  ```bash
  CODEX_SKIP_AUTO_UPDATE_PROMPT=1 codex
  ```

  ### Use a different Codex executable

  ```bash
  CODEX_UPSTREAM=/path/to/codex codex
  ```

  Do not point `CODEX_UPSTREAM` to the wrapper itself, as that would create a launch loop.

  ## Uninstall

  Remove the wrapper:

  ```bash
  rm "$HOME/.local/bin/codex"
  ```

  This does not uninstall the official Codex CLI. To uninstall that separately:

  ```bash
  npm uninstall -g @openai/codex
  ```

  ## License

  This project is available for personal and noncommercial use under the [PolyForm Noncommercial License 1.0.0](LICENSE.md).

  Commercial use requires a separate written commercial license from DevilsNerve. Contact [@DevilsNerve](https://github.com/DevilsNerve) for
  commercial licensing.

  ## Disclaimer

  This is an independent community wrapper and is not an official OpenAI project.
