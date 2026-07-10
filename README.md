# python-templates

### Who this is for

- You are a scientist or engineer at the Allen Institute and want to scaffold a medium to large 
python project that adheres to our [Coding Standards](https://docs.allenneuraldynamics.org/en/latest/policies_practices/software_practices.html).

### Who this might not be for

- You are working on a small python project that is unlikely to be published and does not
require a lot of overhead. You are welcome to use this template, but there may be a learning
curve to be able to use all the tools that will be installed.

- You are working on a set of Jupyter notebooks. This template is primarily for scaffolding
python packages.


### Prerequisites

Please ensure the following tools are installed:

- uv
- git
- GitHub CLI (gh) tool

Install copier by running:
```
uv tool install copier
```

You now have everything you need.

## Usage
To use this template, you can get it directly from Github:
```bash
uvx copier copy https://github.com/AllenNeuralDynamics/python-templates/
```

Or if you want to pick which git ref to copy from:
```bash
uvx copier copy --vcs-ref <git ref> https://github.com/AllenNeuralDynamics/python-templates/library-template <project-name>

```
Note that `--vcs-ref` flag accepts any git ref (a branch name, tag, or commit)

Or if you've cloned this repository and create a project from a local copy:
```bash
copier copy python-templates/library-template .
```

To update an existing project to the latest template version:
```bash
cd <project-name>
uvx copier update
```
Note: The update is from wherever the project was originally generated from. 

### Post installation - Creating a GitHub Repo

- Run:
```
uv sync
gh auth login
git init --initial-branch dev
git add .
git commit -m "feat: initial commit"
gh repo create AllenNeuralDynamics/<project-name> --<public,private,internal> --source=. --push
git checkout -b main
git push origin main
git checkout dev
```
- Please add a Team to the list of collaborators who will help maintain your repository.
- Make sure both a `main` branch and a `dev` branch are created with branch protection rules to 
require a Pull Request before merging.
- Set `Automatically delete head branches` to `true` in the General Settings.
- The template uses reusable workflows for update_badges and tag. Both use a Github App token. However, reusable workflows cannot currently be used as a workflow in a Trusted Publisher. 