# User Personas

## Persona 1: Task Manager

- **Role**: End user who records and tracks their own tasks (todo list).
- **Goals**: Record tasks that need to be completed; track progress toward completion.
- **Behaviors**: Uses Task Tracker when they want to record a todo list and when they want to record progress or completion of a task. Prefers to use their phone; expects mobile-web-optimized experience.
- **Constraints**: Relies on mobile phone access; storage should be local-first (data available on device, works offline or syncs when appropriate).

## Persona 2: Operator

- **Role**: Maintains the application, manages users, and produces usage reporting.
- **Goals**: Keep the application running; manage users (create, disable, roles, etc.); obtain usage data for reporting (e.g. compile in Excel).
- **Behaviors**: Performs user management (e.g. onboard, disable, assign roles). Downloads usage logs and compiles them (e.g. in Excel) for reporting. Does not use Task Tracker for personal task management.
- **Constraints**: Needs access to user-management and usage logs or export; these workflows are outside the core task-list UI (admin/ops tooling or export).

## Usage context

- **When**: Task Tracker is used when the user wants to record a todo list and when they want to record progress or completion of a task.
- **Where**: Optimized for mobile web access; primary device is the user’s phone. Local-first storage so tasks and progress are available on device.
- **How**: Mobile-first web; local-first storage (with sync/export as needed for Operator reporting).
