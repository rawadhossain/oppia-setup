# Installing Oppia (Windows; Python 3)
For detailed installation instructions, see the official wiki: [Installing Oppia (Windows; Python 3)](https://github.com/oppia/oppia/wiki/Installing-Oppia-%28Windows%3B-Python-3%29)
## Run these commands in WSL Ubuntu (home directory, NOT inside oppia)
1. Install pyenv dependencies
```
sudo apt update
sudo apt install -y build-essential libssl-dev zlib1g-dev \
libbz2-dev libreadline-dev libsqlite3-dev wget curl \
llvm libncurses5-dev libncursesw5-dev xz-utils tk-dev

```
2. Install pyenv
```
curl https://pyenv.run | bash
```
3. Add pyenv to your shell
```
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(pyenv init --path)"' >> ~/.bashrc
echo 'eval "$(pyenv init -)"' >> ~/.bashrc
source ~/.bashrc
```

4. Install Oppia’s required Python version
```
pyenv install 3.10.16
pyenv global 3.10.16
```

5. Confirm correct Python
```
python3 --version   # MUST show Python 3.10.16
```

Clone Oppia (still in WSL home directory)
```
git clone https://github.com/rawadhossain/oppia.git
cd oppia
```

## Run these commands Inside the oppia folder only
6. Create venv inside Oppia
```
python3 -m venv venv
source venv/bin/activate
```
7. Verify Python inside venv
```
python3 --version  # MUST still be 3.10.16
```
8. Install Oppia dependencies (inside oppia + venv active)
```
bash scripts/install_prerequisites.sh
```
9. Install Python dev dependencies
```
python3 -m scripts.install_python_dev_dependencies
```

10. Install third-party libraries
```
python3 -m scripts.install_third_party_libs
```

11. Start Oppia (inside oppia + venv active)
```
python3 -m scripts.start --no_browser
```
12. Open browser at:
```
http://localhost:8181
```
13. Keeping everything up, open new wsl ubuntu tab and open in VS Code `code .`

## Every time you return to the project
Always start from WSL Ubuntu terminal (NOT VS Code terminal initially):
```
cd ~/oppia
source venv/bin/activate
python3 -m scripts.start --no_browser
```
Then open: 👉 `http://localhost:8181`

After the server starts, open in VS Code `code .`


## Running Tests (optional, when needed)

Backend tests:
```
python3 -m scripts.run_backend_tests
```

Frontend tests:
```
python3 -m scripts.run_frontend_tests
```
Lint / presubmit check:
```
python3 -m scripts.run_presubmit_checks
```







