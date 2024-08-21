# AutoServerShutdown

AutoServerShutdown is a script designed to automate the shutdown process of multiple remote servers via SSH. It checks each server's availability, sends shutdown commands, and logs the results. This script is ideal for managing a large number of servers, ensuring they are powered off securely and efficiently, while also providing notifications through Telegram.

## Features

- **Server Availability Check**: Automatically checks if the server is available via SSH.
- **SSH Shutdown Command**: Sends a shutdown command to the server if it is reachable.
- **Key Management**: Handles known host key issues by removing outdated keys and retrying the connection.
- **Logging**: Logs all actions taken by the script, including successful and failed shutdown attempts.
- **Telegram Notifications**: Sends notifications to a specified Telegram chat with the results of the shutdown process.

## Installation

1. **Clone the Repository**:

    ```sh
    git clone https://github.com/sqhard08/AutoServerShutdown.git
    cd AutoServerShutdown
    ```

2. **Create Configuration File**:

    Create a file named `config.sh` with your server IPs, SSH parameters, and Telegram bot token and chat ID:

    ```bash
    # config.sh
    
    # List of server IP addresses
    SERVERS=(
        "192.168.1.10"
        "192.168.1.20"
        # Add more servers as needed
    )
    
    # SSH parameters
    SSH_USER="your-ssh-username"
    SSH_PASS="your-ssh-password"
    SSH_PORT=22
    SSH_TIMEOUT=20
    
    # Telegram parameters
    TELEGRAM_BOT_TOKEN="your-telegram-bot-token"
    CHAT_ID="your-telegram-chat-id"
    ```

3. **Make the Script Executable**:

    ```sh
    chmod +x auto_server_shutdown.sh
    ```

4. **Add `config.sh` to `.gitignore`**:

    Ensure that `config.sh` is not uploaded to your repository by adding it to `.gitignore`:

    ```sh
    echo "config.sh" >> .gitignore
    ```

## Example Crontab Entry

To run the script periodically, you can add a cron job:

```sh
*/10 * * * * /path/to/auto_server_shutdown.sh
```
This will run the script every 10 minutes.

## Usage
1. Configure your server IPs and credentials in `config.sh`.
2. Run `auto_server_shutdown.sh` manually or via cron.
3. Check the log file for detailed information on the shutdown process.

## Example Log Output
The script will generate a log file named `server_shutdown.log`, detailing the status of each shutdown attempt. You will also receive notifications via Telegram with the results.
