## Task Tracker CLI
https://roadmap.sh/projects/task-tracker

Simple command line interface (CLI) to track what you need to do, what you have done, and what you are currently working on. Tasks are stored locally in a `tasks.json` file in the current directory. No external libraries are used.

### Requirements
- **Language**: Python 3
- **Storage**: JSON file `tasks.json` (auto-created in the working directory)

### Setup
Make the CLI executable:

```bash
chmod +x ./task-cli
```

Optionally add to PATH:

```bash
ln -s "$(pwd)/task-cli" ~/.local/bin/task-cli
```

### Usage

```bash
# Adding a new task
./task-cli add "Buy groceries"
# Output: Task added successfully (ID: 1)

# Updating and deleting tasks
./task-cli update 1 "Buy groceries and cook dinner"
./task-cli delete 1

# Marking a task as in progress or done
./task-cli mark-in-progress 1
./task-cli mark-done 1

# Listing all tasks
./task-cli list

# Listing tasks by status
./task-cli list done
./task-cli list todo
./task-cli list in-progress
```

### Task Properties
Each task has:
- `id`: unique integer identifier
- `description`: short description
- `status`: one of `todo`, `in-progress`, `done`
- `createdAt`: ISO-8601 timestamp (UTC)
- `updatedAt`: ISO-8601 timestamp (UTC)

### Notes
- The JSON file is created if it does not exist.
- All operations use native filesystem and JSON modules.
- Errors (e.g., invalid IDs, missing args) are reported with helpful messages.

### Examples

```bash
./task-cli add "Read a book"
./task-cli list todo
./task-cli mark-in-progress 2
./task-cli mark-done 2
./task-cli update 2 "Read a book about Python"
./task-cli delete 2
```

