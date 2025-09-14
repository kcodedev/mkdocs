# Taskwarrior Tutorial

Taskwarrior is a command-line task management tool that helps you organize and track your tasks efficiently. This tutorial covers the most common operations you'll need to get started.

## Basic Concepts

- **Tasks**: Individual items you need to complete
- **Projects**: Groups of related tasks
- **Tags**: Labels for categorizing tasks
- **Priorities**: H (High), M (Medium), L (Low)
- **Due dates**: When tasks need to be completed

## Adding Tasks

### Simple Task
```bash
task add "Buy groceries"
```

### Task with Project
```bash
task add project:work "Complete quarterly report"
```

### Task with Due Date
```bash
task add due:today "Call dentist"
task add due:2024-01-15 "Submit tax return"
```

### Task with Priority
```bash
task add priority:H "Fix critical bug"
```

### Task with Tags
```bash
task add +urgent +personal "Renew passport"
```

## Listing Tasks

### View All Tasks
```bash
task list
```

### View Pending Tasks (default)
```bash
task
```

### Filter by Project
```bash
task project:work list
```

### Filter by Tags
```bash
task +urgent list
```

### Filter by Due Date
```bash
task due.before:today list
task due.after:today list
```

### View Completed Tasks
```bash
task completed
```

## Marking Tasks as Done

### Mark by Task ID
First, find the task ID using `task list`, then:
```bash
task 1 done
```

### Mark Multiple Tasks
```bash
task 1,2,3 done
```

### Mark by Description Pattern
```bash
task "Buy groceries" done
```

## Deleting Tasks

### Delete a Task Completely
```bash
task 1 delete
```

**Note**: This permanently removes the task. Use with caution.

### Delete Multiple Tasks
```bash
task 1,2,3 delete
```

## Modifying Tasks

### Change Description
```bash
task 1 modify "Updated task description"
```

### Add Due Date to Existing Task
```bash
task 1 modify due:tomorrow
```

### Change Priority
```bash
task 1 modify priority:M
```

### Add Tags
```bash
task 1 modify +important
```

### Remove Tags
```bash
task 1 modify -urgent
```

## Recurring Tasks

### Create a Daily Recurring Task
```bash
task add recur:daily "Check email"
```

### Create a Weekly Recurring Task
```bash
task add recur:weekly "Team meeting"
```

### Create a Monthly Recurring Task
```bash
task add recur:monthly due:1st "Pay rent"
```

### Recurring Task with Until Date
```bash
task add recur:weekly until:2024-12-31 "Weekly report"
```

## Advanced Operations

### View Task Details
```bash
task 1 info
```

### Search Tasks
```bash
task "keyword" list
```

### Sort Tasks
```bash
task list | sort -k2
```

### Export Tasks
```bash
task export > tasks.json
```

### Import Tasks
```bash
task import tasks.json
```

## Useful Tips

1. **Task IDs**: Use `task list` to see task IDs, which are needed for most operations.

2. **Shortcuts**: You can use partial task descriptions instead of IDs for many commands.

3. **Bulk Operations**: Use ranges like `1-5` or comma-separated lists like `1,3,5`.

4. **Context**: Set up contexts to filter tasks automatically:
   ```bash
   task context define work project:work
   task context work
   ```

5. **Reports**: Taskwarrior has built-in reports. Use `task reports` to see available options.

6. **Configuration**: Customize Taskwarrior by editing `~/.taskrc` or using `task config` commands.

7. **Sync**: For multi-device use, set up synchronization with a service like Taskserver.

## Common Workflows

### Daily Routine
```bash
# Add morning tasks
task add "Review calendar"
task add "Check emails"

# Mark completed tasks
task "Review calendar" done

# List remaining tasks
task
```

### Project Management
```bash
# Create project tasks
task add project:website "Design homepage"
task add project:website "Implement login"
task add project:website "Write documentation"

# View project progress
task project:website list

# Mark project task complete
task "Design homepage" done
```

Remember to regularly review and update your tasks. Taskwarrior's command-line interface makes it fast and efficient once you learn the basic commands.