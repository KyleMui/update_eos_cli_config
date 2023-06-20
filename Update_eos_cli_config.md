# Updating the eos_cli_config

1. Forking the AVD collection
    1. Go to the collection on git
    2. On the top right, click fork

![img](screenshots/Screenshot%202023-06-20%20at%201.41.06%20PM.png)

![img](screenshots/Screenshot%202023-06-20%20at%201.41.10%20PM.png)

2. Creating a branch off of your fork
    1. From the fork, click code and copy the link given
    2. In the terminal:
        1. `git clone <link>`
        2. `git checkout -b <topic-branch-name>`
    3. After finishing with the branch:
        1. `git pull [--rebase] upstream <dev-branch>`
        2. `git push origin <topic-branch-name>`

![img](screenshots/Screenshot%202023-06-20%20at%201.41.15%20PM.png)

![img](screenshots/Screenshot%202023-06-20%20at%201.41.23%20PM.png)

3. Configuring the templates/eos/<<x>config-feature>.j2
    - Creating/Updating the templates/eos/<<x>config-feature>.j2 file
        - Edit the file to change the template
    - If it is a completely new config section, updating eos-intended-config.j2 to reference the newly created  templates/eos/<<x>config-feature>.j2 file
        - Create a file to change the template

![img](screenshots/Screenshot%202023-06-20%20at%201.41.33%20PM.png) **&larr; Where the step 3 directory is**

4. Configuring the templates/documentation/<<x>config-feature>.j2
    - Creating/Updating the templates/documentation/<<x>config-feature>.j2 file
        - Edit a file to change the template
    - If it is a completely new config section, updating eos-device-documentation.j2 to reference the newly created  templates/documentation/<<x>config-feature>.j2 file
        - Add a file to change the template

![img](screenshots/Screenshot%202023-06-20%20at%201.41.43%20PM.png) **&larr; Where the step 4 directory is**

5. Running the pre-commit hook to generate the new documentation in Markdown
    - To manually run pre-commit
        - `pre-commit run`
    - To automatically run pre-commit when committing
        - `pre-commit install`
6.   Updating the molecule test for the eos_cli_config_gen scenario to account for the new feature
    1. If there is no host in the inventory for the feature, then add it
    2. create/update host-var file for the feature
7.   Running the molecule test which should update the documentation and configuration for the feature
    - Look for the scenario that you are working with and the hostname from the git files changed
        - `molecule converge -s <scenario-name> – -l <hostname>`