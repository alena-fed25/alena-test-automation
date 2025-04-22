# Git Workflow Strategy

## Branches

- `main` — stable branch with approved changes only
- `feature/<name>` — feature branch for development

## Workflow Rules

### Local workflow

1. All development is done in the local `feature/<name>` branch.
2. I create or edit files, and commit changes with clear messages:
   ```bash
   git add .
   git commit -m "commit message example"
   ```

### Working with the remote repository

3. Push changes to the remote `feature/<name>` branch:
   ```bash
   git push origin feature/<name>
   ```

4. When a task is complete, I create a Pull Request (PR) from `feature/<name>` to `main` on GitHub:
    - PR title clearly reflects the change (e.g. `Add login tests`)
    - PR description includes what was done and how it was tested

5. The approver reviews the PR:
    - Leaves comments or approves
    - Once approved, the PR is merged into `main` using the GitHub interface

6. If the approver requests changes:
    - I make updates locally in the `feature/<name>` branch
    - Then commit and push again:
      ```bash
      git add .
      git commit -m "fix: address comments on login tests"
      git push origin feature/<name>
      ```
    - The PR on GitHub updates automatically with the new commits

### Merging and final state

7. After merging, the `main` branch contains the final, approved code.
8. I can pull the latest version of `main` if needed:
   ```bash
   git checkout main
   git pull origin main
   ```

### General recommendations

- Never commit directly to `main`
- Always test locally before pushing: `npx cypress run` or `npx cypress open`
- Push only when the code is working and ready for review