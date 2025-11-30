\# 🚀 Telegram History Cleaner (TG-HC)



A powerful, command-line utility built with `Telethon` to safely and precisely delete your own outgoing messages within a specific range defined by text checkpoints in any Telegram chat, group, or channel.



This tool is designed for users who need fine-grained control over their message history without triggering Telegram's rate limits.



---



\## ✨ Features



\* \*\*Precise Range Deletion:\*\* Define the start and end of the deletion range using specific text phrases (checkpoints).

\* \*\*Safety Measures:\*\* Implements random, short delays between message deletions and longer pauses every 100 messages to prevent account suspension due to Telegram's rate limits.

\* \*\*Automatic Localization (i18n):\*\* Automatically detects your operating system's language settings and loads the corresponding interface text (e.g., `ru.py`, `de.py`).

\* \*\*Channel ID Conversion:\*\* Automatically handles large public channel IDs (e.g., `100xxxxxxxxxx`) by converting them to the required format (`-100xxxxxxxxxx`).

\* \*\*Minimalist Interface:\*\* Clean, focused menu designed solely for history management (stats function was removed for performance).



---



\## 🛑 Important Limitation (Checkpoint Text Search)



\*\*The current version uses text search to define the range, which has a critical limitation:\*\*



When setting the \*\*End Checkpoint\*\* (the oldest message to delete), the tool currently finds the \*\*newest message\*\* containing that phrase within the scanned history.



\* \*\*Problem:\*\* If the phrase you use (e.g., "hello") is repeated many times in the chat, the deletion range will be \*\*cut short\*\* and will not reach the oldest occurrences of that phrase.

\* \*\*Temporary Solution:\*\* Always use \*\*unique, long, or highly specific phrases\*\* for both the Start and End Checkpoints to guarantee the range is set correctly.



> 💡 \*\*Future Development:\*\* This issue will be resolved by replacing text-based checkpoints with the more accurate \*\*Message ID (or Message Link)\*\* input.



---



\## 🛠️ Installation \& Setup



\### Prerequisites



\* Python 3.8+

\* A Telegram API Key (`API\_ID` and `API\_HASH`). You can get one from \[my.telegram.org](https://my.telegram.org).



\### Steps



1\.  \*\*Clone the Repository:\*\*

&nbsp;   ```bash

&nbsp;   git clone \[https://github.com/YourUsername/tg\_manager](https://github.com/YourUsername/tg\_manager)

&nbsp;   cd tg\_manager

&nbsp;   ```



2\.  \*\*Create Virtual Environment (Recommended):\*\*

&nbsp;   ```bash

&nbsp;   python -m venv venv

&nbsp;   source venv/bin/activate  # On Windows: venv\\Scripts\\activate

&nbsp;   ```



3\.  \*\*Install Dependencies:\*\*

&nbsp;   ```bash

&nbsp;   pip install -r requirements.txt

&nbsp;   # You will need Telethon and python-dotenv

&nbsp;   ```



4\.  \*\*Configure Environment (`.env` file):\*\*

&nbsp;   Create a file named \*\*`.env`\*\* in the root directory (`tg\_manager/`) and populate it with your Telegram credentials:



&nbsp;   ```env

&nbsp;   # .env

&nbsp;   API\_ID=YOUR\_API\_ID\_HERE

&nbsp;   API\_HASH=YOUR\_API\_HASH\_HERE

&nbsp;   SESSION\_NAME=my\_session\_name

&nbsp;   ```



---



\## 🚀 Usage



1\.  \*\*Run the script:\*\*

&nbsp;   ```bash

&nbsp;   python main.py

&nbsp;   ```



2\.  \*\*Login:\*\* The first time you run the script, `Telethon` will prompt you to enter your phone number, password, and the code sent by Telegram. This creates the session file (`my\_session\_name.session`).



3\.  \*\*Enter Target ID:\*\* Input the numerical ID of the user, group, or channel you wish to clean.

&nbsp;   \* \*\*User/Group ID:\*\* Standard numerical ID (e.g., `123456789`).

&nbsp;   \* \*\*Public Channel ID:\*\* Use the large positive ID (e.g., `1001641860103`), and the script will automatically convert it to the required negative format.



4\.  \*\*Select Option 1 (Delete History):\*\* Follow the prompts to enter your unique phrases for the Start and End Checkpoints.



---



\## 🌐 Supported Languages



The program automatically detects your system's locale and loads the corresponding language file from `src/language/`.



Currently supported languages:



\* \*\*English\*\* (`en.py`) - Default fallback.

\* \*\*Russian\*\* (`ru.py`)

\* \*\*...\*\* (Add more language codes here)



To add a new language (e.g., Ukrainian), simply create a file named `uk.py` inside the `src/language/` directory and translate all string constants.

