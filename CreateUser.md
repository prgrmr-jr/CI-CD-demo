# Creating a New User on Linux (Ubuntu) :Optional

To create a new superuser in Linux Ubuntu, follow these steps:

1. **Open Terminal**:

2. **Add a New User**: Replace `username` with your desired username and password.
    ```sh
    sudo adduser <username>
    ```

3. **Add User to Sudo Group**: This grants the new user superuser privileges.
    ```sh
    sudo usermod -aG sudo <username>
    ```

4. **Verify the New Superuser**: Switch to the new user and check sudo access.
    ```sh
    su - <username>
    sudo whoami
    ```
