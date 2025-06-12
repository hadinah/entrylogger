# entrylogger
A Python based module to Mark Entry, specificaly built for workspace's

## Overview

EntryLogger is a simple yet efficient Python module designed to track entry and exit times for users in a workspace. It integrates with databases like Supabase to log check-in and check-out times. This module can be particularly useful for managing employee or student attendance, monitoring work hours, or even just managing time logs for a team or personal use.

## Features

- **Track Entry and Exit Times:** Log when a user enters or exits the workspace.
- **User-Specific Logs:** Entries are stored for individual users, making it easy to monitor specific users' work hours.
- **Dynamic Time Tracking:** The check-in time is automatically stored when the user first enters, and the checkout time is recorded when the user leaves.
- **Integration with Supabase:** The module supports seamless integration with Supabase for managing and storing logs.

## Installation

### Prerequisites
1. You need to have Python 3.6 or higher installed on your system.
2. Install the required libraries using `pip`:

```bash
pip install -r requirements.txt
```

3. Setup .env

Before you can use the module, ensure you have the required environment variables set up for Supabase integration. Create a .env file in the root of your project with the following variables:
```python
SUPABASE_URL=your_supabase_url
SUPABASE_KEY=your_supabase_key (service key/secret)
SUPABASE_DB_URL=your_supabase_db_url
```
Replace your_supabase_url, your_supabase_key and your_supabase_db_url with your actual Supabase project credentials.
Installation via pip

4. Installing the module.

You can install the module directly from pip:
```bash
pip install entrylogger
```
Alternatively, you can install module directly from git:
```bash
pip install git+https://github.com/hadinah/entrylogger.git
```
## Usage
1. Setting up the environment:

Ensure your .env file is properly configured with the correct Supabase credentials (SUPABASE_URL and SUPABASE_KEY, SUPABASE_DB_URL).

2. Basic Usage Example:

Here's an example of how you can use the module to track user entry and exit times:
```python
import entrylogger

# Log entry (Check-in)
entrylogger.mark_entry(user_id="user-id")

# Log exit (Check-out)
entrylogger.mark_exit(user_id="user-id")
```

3. Integrating with Supabase:

Ensure your Supabase project is set up, and the database tables (entry_logs, task_logs, user_logs, etc.) are created. You can use the script provided in the repository to automatically create these tables.
4. Customizing the Module:

If needed, you can extend and customize the module to fit your use case. Add custom logic, like tracking user tasks or integrating with other services.
Database Schema
1. entry_logs Table:

Stores user entries and exits.
Column	Type	Description
entry_id	time without time zone	Unique identifier for the entry time
workday_id	date	The workday date
user_id	uuid	User ID from your system
entry	boolean	Whether the entry is check-in (True) or check-out (False)
2. task_logs Table:

Stores the tasks logged by users.
Column	Type	Description
workday_id	date	The workday date
user_id	uuid	User ID from your system
name	text	Name of the task
tags	text[]	Tags related to the task
3. user_logs Table:

Stores check-in and check-out information for users.
Column	Type	Description
user_id	uuid	User ID from your system
workday_id	date	The workday date
checkin_time	timestamp with time zone	The check-in time
checkout_time	timestamp with time zone	The check-out time
Contributing

Feel free to contribute! Here's how you can help:

    Open Issues: Report bugs or suggest new features.

    Fork and Pull Requests: Fork the repository, make your changes, and submit a pull request.

### License

This project is licensed under the GNU General Public License v3.0 - see the LICENSE file for details.
Acknowledgements

    Supabase for providing the back-end integration.

    Python and all the awesome libraries it offers for development.
