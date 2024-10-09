# Update Linux System and Install Required Packages

Before setting up Node.js, it is recommended to update your Linux system and install the required packages.

## Update System Packages

```sh
sudo apt update
sudo apt upgrade
```

# Setting Up Node.js Using NVM

## Prerequisites
- A Unix-based system (Linux or macOS)
- Curl or Wget installed

## Steps

1. **Install NVM (Node Version Manager)**:
    ```sh
    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.4/install.sh | bash
    source ~/.bashrc
    ```

2. **Get list of Node**:
    ```sh
    nvm ls-remote
    ```

3. **Install Node.js**:
    ```sh
    nvm install v20.x.x
    ```
    Change `v20.x.x` to the desired version.

4. **Verify Installation**:
    ```sh
    node -v
    npm -v
    nvm ls
    ```

## Optional: Installing Docker

### Docker Installation on Ubuntu

Follow these steps to install Docker on your Ubuntu system.

### Step 1: Update Package List and Install Prerequisites

```sh
sudo apt update
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```

### Step 2: Add Docker’s Official GPG Key

```sh
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

### Step 3: Add the Docker Repository

```sh
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

### Step 4: Update Package List Again and Install Docker

```sh
sudo apt update
sudo apt install docker-ce
```

### Step 5: Verify Docker Installation

```sh
sudo systemctl status docker
```

Docker should now be installed and running on your Ubuntu system.
