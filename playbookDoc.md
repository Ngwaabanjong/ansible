# ANSIBLE PLAYBOOK
- Just like a recipe tells you how to cook a meal step by step, an Ansible playbook tells your computer how to do certain tasks step by step.
- This will make your computer follow the steps in the playbook, just like you would follow a recipe to cook a meal!
### Key Points
- **Playbook**: A list of steps (tasks) written in YAML format.
- **Hosts**: Where the tasks will run.
- **Become**: Whether special permissions are needed.
- **Tasks**: The steps to perform.
- **Modules**: Tools like `file` and `apt` that do specific jobs.

simple way to understand and write an Ansible playbook:

### Step-by-Step Guide

1. **Start with a Plan**: Just like you decide what meal you want to cook, decide what tasks you want your computer to do. For example, let's say you want your computer to create a file and install a program.

2. **Write the Playbook**: This is like writing down the recipe.

### Example Playbook

Let's write a simple playbook to create a file called `example.txt` and install a program called `git`.

Here's how you can write it:

1. **Start with three dashes**: This tells the computer that this is the start of the playbook.

    ```yaml
    ---
    ```

2. **Give a name to the playbook**: This is like the title of your recipe.

    ```yaml
    - name: Simple Playbook
    ```

3. **Hosts**: Tell the playbook where to run. For now, we will use `localhost`, which means it will run on your own computer.

    ```yaml
      hosts: localhost
    ```

4. **Become**: This is like saying you need special permissions (like a parent in the kitchen). `yes` means you need these permissions.

    ```yaml
      become: yes
    ```

5. **Tasks**: List out the steps you want to do.

    ```yaml
      tasks:
    ```

6. **Task 1 - Create a file**:

    ```yaml
        - name: Create a file
          file:
            path: /home/username/example.txt
            state: touch
    ```

    Here’s what each part means:
    - `- name: Create a file`: Give a name to this step.
    - `file:`: This tells the computer we are going to do something with a file.
    - `path: /home/username/example.txt`: This is where the file will be created.
    - `state: touch`: This tells the computer to create the file if it doesn’t already exist.

7. **Task 2 - Install a program**:

    ```yaml
        - name: Install git
          apt:
            name: git
            state: present
    ```

    Here’s what each part means:
    - `- name: Install git`: Give a name to this step.
    - `apt:`: This is the module we use to install programs on Debian-based systems (like Ubuntu).
    - `name: git`: This is the name of the program we want to install.
    - `state: present`: This tells the computer to make sure the program is installed.

### Putting It All Together

Here’s the complete playbook:

```yaml
---
- name: Simple Playbook
  hosts: localhost
  become: yes
  tasks:
    - name: Create a file
      file:
        path: /home/username/example.txt
        state: touch

    - name: Install git
      apt:
        name: git
        state: present
```

### Running the Playbook

To run this playbook, you save it in a file called `simple_playbook.yml` and then run the following command in your terminal:

```bash
ansible-playbook simple_playbook.yml
```

I hope this makes writing an Ansible playbook easier to understand!
