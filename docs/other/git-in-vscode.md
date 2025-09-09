# Using Git in Visual Studio Code

This guide provides a comprehensive overview of using Git version control within Visual Studio Code (VS Code).

## Prerequisites

Before you begin, ensure you have the following installed:

- **Visual Studio Code**: Download from [code.visualstudio.com](https://code.visualstudio.com/).
- **Git**: Download from [git-scm.com](https://git-scm.com/). Follow the installation instructions for your operating system.
- **Git Graph Extension** (optional but recommended): Install from the VS Code Extensions marketplace for a visual representation of your Git history.

## Initial Setup

1. Open VS Code.
2. Open the folder containing your project (File > Open Folder).
3. If the folder is not a Git repository, initialize it:
   - Open the terminal in VS Code (View > Terminal).
   - Run: `git init`
4. Configure Git with your details:
   ```
   git config --global user.name "Your Name"
   git config --global user.email "your.email@example.com"
   ```

## Basic Git Operations in VS Code

### Staging Changes

1. Make changes to your files.
2. In the Source Control view, you'll see a list of changed files.
3. Click the "+" icon next to a file to stage it, or "+" next to "Changes" to stage all.

### Committing and Pushing Changes

1. After staging, enter a commit message in the text box at the top.
2. Click the commit button.
3. Click sync button to push remote.

### Pushing and Pulling

... to add

## Branching and Merging

### Creating a Branch

1. Click on the branch name in the bottom-left corner of VS Code.
2. Select "Create new branch".
3. Enter a branch name and press Enter.

### Switching Branches

1. Click the branch name in the bottom-left corner.
2. Select the desired branch from the list.

### Merging Branches

1. Switch to the target branch (e.g., main).
2. Open the Source Control view.
3. Click the "..." menu.
4. Select "Branch" > "Merge Branch".
5. Choose the branch to merge.

## Resolving Merge Conflicts

When conflicts occur during a merge:

1. VS Code will highlight conflicted files.
2. Open the conflicted file.
3. Look for conflict markers: `<<<<<<<`, `=======`, `>>>>>>>`.
4. Edit the file to resolve the conflict.
5. Stage the resolved file.
6. Commit the merge.

## Using Git Graph

With the Git Graph extension:

1. Open the Command Palette (Ctrl+Shift+P).
2. Type "Git Graph: View Git Graph" and select it.
3. This provides a visual interface for:
   - Viewing commit history
   - Creating and deleting branches
   - Rebasing commits
   - Cherry-picking
   
   To add Git Graph to the left sidebar, run "Git Graph: Add Git Graph View to Explorer" from the Command Palette.

## Advanced Features

### Stashing Changes

1. If you have uncommitted changes and need to switch branches:
   - Click the "..." menu in Source Control.
   - Select "Stash" > "Stash".
2. To apply stashed changes later:
   - Select "Stash" > "Apply Stash".

### Viewing Diffs

1. In the Source Control view, click on a file to see the diff.
2. Use the inline diff view to review changes before committing.

### Ignoring Files

1. Create a `.gitignore` file in your repository root.
2. Add patterns for files/folders to ignore (e.g., `node_modules/`, `*.log`).
3. VS Code will automatically suggest ignoring common files.

## Best Practices

- Commit often with clear, descriptive messages.
- Use branches for new features or bug fixes.
- Pull regularly to stay up-to-date with the remote repository.
- Review diffs before committing.
- Use meaningful branch names (e.g., `feature/add-login`, `bugfix/fix-header`).

## Troubleshooting

- **Authentication Issues**: Ensure your Git credentials are set up correctly. For GitHub, you can use a Personal Access Token.
- **Detached HEAD State**: This occurs when you're not on a branch. Use the branch selector to switch to a branch.
- **Untracked Files**: These are new files not yet added to Git. Stage them to include in commits.
- **Source Control Icon Not Visible**: If the Git icon in the left sidebar is missing, go to View > Appearance > Show Source Control, or right-click the sidebar and ensure "Source Control" is checked. Verify Git is installed (`git --version` in terminal) and the workspace is a Git repository. Check VS Code settings for "git.enabled" and ensure it's set to `true`. Reload VS Code if needed.

For more detailed information, refer to the official Git documentation at [git-scm.com/doc](https://git-scm.com/doc) and VS Code's Git documentation at [code.visualstudio.com/docs/sourcecontrol/overview](https://code.visualstudio.com/docs/sourcecontrol/overview).