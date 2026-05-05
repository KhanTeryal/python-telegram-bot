# Base Telegram Bot E-Commerce

This is a simple base Telegram bot project built with Python, designed with an extensible plugin architecture, a robust role-based access control system, and a customizable e-commerce platform.

## Key Features

- **Dynamic Plugin Architecture**: Easily add new functionality and commands by creating new Python files in the `plugins` directory. A decorator-based system automatically registers new commands when the bot starts.
- **E-Commerce Platform**: Users can create their own virtual stores, add products, and sell them to other users. The purchasing process is handled through interactive inline keyboards.
- **Role & Access Management**: A secure role system (`owner`, `store`, `premium`, `free`) protects critical commands. Roles can be assigned with a time duration and will automatically expire.
- **JSON Database**: Uses simple JSON files to store and manage user and transaction data, making it easy to inspect and back up.
- **Secure Configuration**: Keeps API keys and sensitive configurations separate from the source code using a `.env` file.

## Architecture

The project is structured with clear separation of concerns for maintainability and scalability:

- **`main.py`**: Entry point that initializes the bot and loads all plugins.
- **`/plugins`**: Each file represents a feature or a set of bot commands. Most of the functional logic resides here.
- **`/core`**: Contains core business logic, including user management (`User_Manager.py`), security (`security.py`), and utility functions.
- **`/data`**: Directory where JSON database files (`users.json`, `transaction.json`) are stored.

## Installation & Setup

Follow these steps to run the bot locally:

### 1. Clone the Repository

```bash
git clone https://github.com/KhanTeryal/python-telegram-bot.git
cd python-telegram-bot
```

2.  **Create a Virtual Environment (Recommended)**

    ```bash
    python -m venv venv
    ```

    - Windows: `venv\Scripts\activate`
    - macOS/Linux: `source venv/bin/activate`

3.  **Install Dependencies**

    ```bash
    pip install -r requirements.txt
    ```

4.  **Configure Environment Variables**
    Create a file named `.env` in the root directory and fill it with the following:

    ```env
    token=YOUR_TELEGRAM_BOT_TOKEN
    OWNER_ID=YOUR_TELEGRAM_ID
    ```

    - `token`: Obtained from BotFather on Telegram
    - `OWNER_ID`: Your Telegram user ID, which can be retrieved using the /id command after the bot is running.

5.  **Run the Bot**
    ```bash
    python main.py
    ```
    If everything is set up correctly, you will see the message "Bot is running..." in the terminal.

## Command List

Below is a list of available commands in the bot, categorized by function.

#### General Commands

- `/start` - Start interaction with the bot.
- `/register` - Register yourself in the bot database.
- `/list` - Display all available commands.
- `/id` - Get your Telegram user ID.

#### E-Commerce Commands

- `/create_store <nama> <deskripsi>` - Create your own virtual store.
- `/create_produck <nama> <harga> <deskripsi>` - Add a new product to your store.
- `/produck` - View the list of products in your store.
- `/buy <nama_toko>` - Browse and purchase products from other users.
- `/my_orders` - View your purchase history.

#### Admin Commands (Owner Only)

- `/promote <user_id> <role> <duration> <unit>` - Promote a user to a specific role.
- `/demote <user_id>` - Dmote a user back to the "free" role.

## Technologies Used

- **Python 3**
- **python-telegram-bot**: Main library for interacting with the Telegram Bot API.
- **python-dotenv**: For managing environment variables.

