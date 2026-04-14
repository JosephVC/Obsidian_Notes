
https://ubuntuhandbook.org/index.php/2024/03/pip-install-error-ubuntu-2404/

Pipx is an alternative command line tool to install and run Python applications in isolated environments. It’s however for **Pythons apps only**.

To install and setup pipx, simply run command:

sudo apt install pipx

pipx ensurepath

[![](https://ubuntuhandbook.org/wp-content/uploads/2024/03/apt-pipx-700x438.webp)](https://ubuntuhandbook.org/wp-content/uploads/2024/03/apt-pipx.webp)

Then you can install a Python app via pipx, for example cowsay, use command:

pipx install cowsay

Then run it via:

pipx run cowsay --text "Mooo"

And use command to uninstall Python package:

pipx uninstall cowsay

For more about pipx, either run `pipx --help` or go to its [project page](https://github.com/pypa/pipx).