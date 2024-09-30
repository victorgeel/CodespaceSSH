## 🧸GitHub Codespaces and connecting from Termux on Android:🧸

### Fork my blank repo
[github](https://github.com/codespaces)
### You didn't need any coding level.

# Setting Up SSH Server in GitHub Codespaces

This guide will help you set up an SSH server in GitHub Codespaces and connect to it using Termux on Android.

## Prerequisites

- A GitHub account.
- A blank GitHub repository.
- Termux installed on your Android device.

## Setting Up SSH Server in GitHub Codespaces

1. **Create a Codespace**  
   Go to your GitHub repository and create a new
   [codespace](https://github.com/codespaces)

3. **Install OpenSSH Server**  
   Open the terminal in your Codespace and run the following commands to install the SSH server:

   ```bash
   sudo apt update
   sudo apt install openssh-server

### 3. Start the SSH Server
Start the SSH service using:

``` bash
sudo service ssh start
```


4. Check SSH Status
Ensure the SSH server is running:

```bash
sudo service ssh status
```


### 5. Get the Codespace IP Address
Find the IP address of your Codespace by running:

```bash
hostname -I
```


### 6. Set Up SSH Keys
If you don't have an SSH key pair on your local machine, create one using:

```sh
ssh-keygen
```

### ** Copy the public key to your Codespace's authorized_keys file. Use the command below in your Codespace:

```bash
echo "your-public-key" >> ~/.ssh/authorized_keys
```

### ** Replace "your-public-key" with the content of your public key (found in ~/.ssh/id_rsa.pub on your local machine).


## 7. Configure SSH
### Ensure that the SSH configuration allows key-based authentication. Edit the SSH config file (/etc/ssh/sshd_config) and make sure the following lines are present and uncommented:

```txt
PubkeyAuthentication yes
AuthorizedKeysFile %h/.ssh/authorized_keys
```

After making changes, restart the SSH service:

```sh
sudo service ssh restart
```



## Connecting from Termux or terminus on Android

### 1. Install OpenSSH in Termux
Open Termux and install the OpenSSH package:

```bash
pkg update
pkg install openssh
```


### 2. Connect to Your Codespace
Use the SSH command with the IP address of your Codespace:

```bash
ssh user@your-codespace-ip
```

### - Replace user with the username (usually root in Codespaces) and your-codespace-ip with the actual IP address you obtained earlier.


## 3. Accept the Host Key
### The first time you connect, you may be prompted to accept the host key. Type yes to continue.



# Notes

### Public Access: Depending on your Codespace settings, you may need to configure firewall rules to allow incoming SSH connections.

### Keep Alive: Since Codespaces can time out, you may want to look into settings that prevent the session from closing if you're frequently accessing it.

## Screenshots

### Codespace
![Screenshot of Codespace](https://github.com/victorgeel/CodespaceSSH/blob/main/Screenshot_20240930_192540_Chrome.png)

### Settings
![Screenshot of Settings](https://github.com/victorgeel/CodespaceSSH/blob/main/Screenshot_20240930_192614_Chrome.png)


## Conclusion

## Please use with your own dissociation.I do not know that cost was free or paid.

### With these steps, you should be able to connect to your GitHub Codespace via SSH from Termux on your Android device. If you encounter any issues, ensure your SSH server is running and that you're using the correct IP address and credentials.
