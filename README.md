# Easier Developer Experience

A collection of Cursor Commands designed to streamline common development workflows and make your daily coding tasks more efficient.

## 🎯 What is This?

This repository contains pre-configured Cursor Commands that automate repetitive development tasks, reduce context switching, and help you maintain best practices. Instead of remembering complex git workflows or lengthy command sequences, simply use natural language commands in Cursor.

## 📚 What are Cursor Commands?

Cursor Commands are markdown files stored in `.cursor/commands/` that define automated workflows for the Cursor AI IDE. When you trigger a command (e.g., "run push"), Cursor's AI assistant executes the defined steps automatically, handling permissions, error cases, and user interactions intelligently.

## 🚀 Available Commands

### Git Workflow Commands

#### `run new branch`

Creates a new git branch following best practices:

- Saves any uncommitted work on your current branch
- Switches to main and updates it from remote
- Creates a fresh feature branch from the latest main
- Handles branch naming (auto-converts spaces to hyphens)
- Validates the new branch was created successfully

**Why use it:** Ensures you always start new features from an up-to-date main branch without losing any work.

---

#### `run push`

Pushes your changes to the current branch with a complete git workflow:

- Shows you what branch you're on
- Checks for uncommitted changes and stages them
- Prompts for a commit message
- Commits and pushes changes
- Automatically sets upstream for new branches
- Handles common push errors gracefully

**Why use it:** Combines staging, committing, and pushing into one seamless operation with intelligent error handling.

---

#### `run delete branch`

Safely deletes a local git branch after review and merge:

- Confirms the branch was successfully reviewed and merged (with congratulations! 🎉)
- Automatically switches to main if you're on the branch to be deleted
- Uses safe deletion by default (`-d` flag)
- Optionally force deletes if you confirm
- Pulls the latest changes to main after deletion
- Verifies the branch was removed

**Why use it:** Keeps your local repository clean while preventing accidental deletion of unmerged work.

---

### Development Environment Commands

#### `run start`

Starts your complete local development environment:

- Launches backend services with automatic error handling
- Offers to enable frontend live reloading (Ember server)
- Automatically runs install script if services fail to start
- Handles authentication errors (expired GitHub tokens)
- Provides interactive prompts when needed
- Gives you the application URL when ready

**Why use it:** One command to get your entire development environment running, with intelligent error recovery.

---

#### `run stop`

Gracefully shuts down your development environment:

- Stops the frontend server (port 4201)
- Verifies the port is freed
- Stops all backend services
- Confirms clean shutdown

**Why use it:** Ensures all processes are properly terminated without leaving zombie processes or locked ports.

---

## 💡 How to Use

1. **Open your project in Cursor**
2. **Trigger a command by typing in the chat:**
   - "run new branch"
   - "run push"
   - "run delete branch"
   - "run start"
   - "run stop"
3. **Follow the prompts** - Cursor's AI will guide you through each step

## 📁 Repository Structure

```
.cursor/
└── commands/
    ├── create-new-branch.md
    ├── push-changes-to-branch.md
    ├── delete-branch.md
    ├── start.md
    └── stop.md
```

## 🛠️ Installation

To use these commands in your own projects:

1. **Clone this repository:**

   ```bash
   git clone https://github.com/yourusername/easier-dev-exp.git
   ```

2. **Copy the `.cursor` directory** to your project:

   ```bash
   cp -r easier-dev-exp/.cursor /path/to/your/project/
   ```

3. **Open your project in Cursor** and the commands will be automatically available

## 🎨 Customization

Feel free to modify these commands for your specific workflow:

1. Navigate to `.cursor/commands/` in your project
2. Edit the markdown files to adjust steps, prompts, or behaviors
3. Commands are automatically reloaded by Cursor

## 🤝 Contributing

Have ideas for new commands or improvements? Contributions are welcome!

1. Fork this repository
2. Create a new branch (`run new branch` 😉)
3. Add your command or improvements
4. Submit a pull request

## 📝 Command Creation Tips

When creating your own Cursor Commands:

- **Be specific:** Define exact commands and their expected outputs
- **Handle errors:** Include fallback steps for common failure scenarios
- **Be interactive:** Ask users for confirmation when making destructive changes
- **Add context:** Explain what's happening at each step
- **Request permissions:** Explicitly state when `all` or `network` permissions are needed

## 🌟 Benefits

- **Consistency:** Everyone on your team follows the same workflow
- **Speed:** Automate multi-step processes into single commands
- **Safety:** Built-in checks prevent common mistakes
- **Learning:** New team members learn best practices through guided workflows
- **Focus:** Spend less time on tooling, more time on coding

## 📄 License

MIT License - feel free to use these commands in your projects!

## 🙏 Acknowledgments

Built with ❤️ using [Cursor](https://cursor.sh/) - the AI-first code editor.

---

**Made with Cursor Commands** - Making developer experience just a little bit easier, one command at a time.
