---
name: agent-instruction-creator-agent
description: Create or refactor the AGENTS.md file, .github/copilot-instructions.md file, and .ai-context folder for this repository to be a concise, high-signal guide for coding agents.
---

Your task is to "onboard" this repository to Copilot cloud agent by creating the following structure:

1. `.ai-context/` folder in the repository root containing:
   - `docs/PROJECT_OVERVIEW.md` - Contains the generated project overview content
   - `rules/general.rule.md` - Contains the general development guidelines
2. `.github/copilot-instructions.md` - Points to the ai-context files
3. `AGENTS.md` - Points to the ai-context files

You will do this task only one time per repository and doing a good job can SIGNIFICANTLY improve the quality of the agent's work, so take your time, think carefully, and search thoroughly before writing the instructions.

<Goals>
- Reduce the likelihood of a cloud agent pull request getting rejected by the user due to generating code that fails the continuous integration build, fails a validation pipeline, or having misbehavior.
- Minimize bash command and build failures.
- Allow the agent to complete its task more quickly by minimizing the need for exploration using grep, find, str_replace_editor, and code search tools.
</Goals>

<Limitations>
- Instructions must be no longer than 2 pages.
- Instructions must not be task specific.
</Limitations>

<FilesToCreate>

## 1. `.ai-context/docs/PROJECT_OVERVIEW.md`

Generate and write the following content into this file:

<HighLevelDetails>
- A summary of what the repository does.
- High level repository information, such as the size of the repo, the type of the project, the languages, frameworks, or target runtimes in use.
</HighLevelDetails>

<BuildInstructions>
- For each of bootstrap, build, test, run, lint, and any other scripted step, document the sequence of steps to take to run it successfully as well as the versions of any runtime or build tools used.
- Each command should be validated by running it to ensure that it works correctly as well as any preconditions and postconditions.
- Try cleaning the repo and environment and running commands in different orders and document errors and misbehavior observed as well as any steps used to mitigate the problem.
- Run the tests and document the order of steps required to run the tests.
- Make a change to the codebase. Document any unexpected build issues as well as the workarounds.
- Document environment setup steps that seem optional but that you have validated are actually required.
- Document the time required for commands that failed due to timing out.
- When you find a sequence of commands that work for a particular purpose, document them in detail.
- Use language to indicate when something should always be done. For example: "always run npm install before building".
- Record any validation steps from documentation.
</BuildInstructions>

<ProjectLayout>
- A description of the major architectural elements of the project, including the relative paths to the main project files, the location of configuration files for linting, compilation, testing, and preferences.
- A description of the checks run prior to check in, including any GitHub workflows, continuous integration builds, or other validation pipelines.
- Document the steps so that the agent can replicate these itself.
- Any explicit validation steps that the agent can consider to have further confidence in its changes.
- Dependencies that aren't obvious from the layout or file structure.
- Finally, fill in any remaining space with detailed lists of the following, in order of priority: the list of files in the repo root, the contents of the README, the contents of any key source files, the list of files in the next level down of directories, giving priority to the more structurally important and snippets of code from key source files, such as the one containing the main method.
</ProjectLayout>

## 2. `.ai-context/rules/general.rule.md`

Create this file with the following exact content:

```markdown
# General Development Guidelines

## Code Generation

Follow clean architecture principles with proper separation of concerns.

### Coding Standards

- TODO

### Input Validation

- TODO

### Database

- TODO

## File Editing

1.  When asked to edit, improve, or refactor a file, always edit the original file in its existing location
2.  Before making changes, analyze the file's structure and coding conventions
3.  Never create a duplicate or replacement file unless explicitly instructed to do so
4.  Preserve imports, dependencies, and file structure unless changes to these are specifically requested
5.  When editing, focus on the specific sections that need changes instead of rewriting the entire file

## Testing Requirements

## Commit Messages

Follow the [Conventional Commits](https://www.conventionalcommits.org/) specification. The project uses commitlint with `@commitlint/config-conventional` to enforce this standard.

### Format
```

<type>(<scope>): <subject>

```

### Rules

1.  **Type**: Must be one of the following:
- `feat`: A new feature
- `fix`: A bug fix
- `docs`: Documentation only changes
- `style`: Changes that do not affect the meaning of the code (white-space, formatting, etc.)
- `refactor`: A code change that neither fixes a bug nor adds a feature
- `perf`: A code change that improves performance
- `test`: Adding missing tests or correcting existing tests
- `build`: Changes that affect the build system or external dependencies
- `ci`: Changes to CI configuration files and scripts
- `chore`: Other changes that don't modify src or test files
- `revert`: Reverts a previous commit

1.  **Scope** (optional): The scope of the change in camelCase (e.g., `onlineCustomer`, `offlineCustomer`, `migration`, `config`)

1.  **Subject**:
- Use imperative, present tense (e.g., "add" not "added" or "adds")
- Don't capitalize the first letter
- No period (.) at the end for one-sentence commit messages
- Keep it concise (max 100 characters)

### Examples

```

feat(onlineCustomer): add phone to online customer table

````

## 3. `.github/copilot-instructions.md` and `AGENTS.md`

Both files should include the following content at the top:

```markdown
## Read first

Read

- `.ai-context/docs/PROJECT_OVERVIEW.md` for project description
- `.ai-context/rules/general.rule.md` for basic rule while doing updates
````

</FilesToCreate>

<StepsToFollow>
1. Create the `.ai-context/docs/` directory structure
2. Create the `.ai-context/rules/` directory structure
3. Perform a comprehensive inventory of the codebase:
   - Search for and view README.md, CONTRIBUTING.md, and all other documentation files
   - Search the codebase for build steps and indications of workarounds like 'HACK', 'TODO', etc.
   - All scripts, particularly those pertaining to build and repo or environment setup
   - All build and actions pipelines
   - All project files
   - All configuration and linting files
4. For each file found, think: are the contents or the existence of the file information that the cloud agent will need to implement, build, test, validate, or demo a code change?
5. Generate the PROJECT_OVERVIEW.md content based on your analysis and write it to `.ai-context/docs/PROJECT_OVERVIEW.md`
6. Create `.ai-context/rules/general.rule.md` with the exact content specified above
7. Create `.github/copilot-instructions.md` with the "Read first" section
8. Create `AGENTS.md` with the "Read first" section
9. Document any errors encountered as well as the steps taken to work-around them
10. Finally, explicitly instruct the agent to trust the instructions and only perform a search if the information in the instructions is incomplete or found to be in error
</StepsToFollow>
