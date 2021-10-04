# Setting up NodeJS, NPM and Yarn

## Installation

### One line command for lazy person

```bash
curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash - && sudo apt install -y nodejs && sudo apt install -y gcc g++ make && curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | gpg --dearmor | sudo tee /usr/share/keyrings/yarnkey.gpg >/dev/null && echo "deb [signed-by=/usr/share/keyrings/yarnkey.gpg] https://dl.yarnpkg.com/debian stable main" | sudo tee /etc/apt/sources.list.d/yarn.list && sudo apt update && sudo apt install -y yarn
```

### Step by step installation

 - Add node from NodeSource
```bash
curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -
```

 - Install nodejs
```bash
sudo apt install -y nodejs
```

 - Install build tools
```bash
sudo apt install -y gcc g++ make
```

 - Add yarn
```bash
curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | gpg --dearmor | sudo tee /usr/share/keyrings/yarnkey.gpg >/dev/null
```
```bash
echo "deb [signed-by=/usr/share/keyrings/yarnkey.gpg] https://dl.yarnpkg.com/debian stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
```

 - Update
```bash
sudo apt update
```

 - Install yarn
```bash
sudo apt install -y yarn
```
 
