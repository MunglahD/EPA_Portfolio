### 1. Write a Ruby or Bash script that will print usernames of all users on a Linux system together with their home directories. Here's some example output:

```
gitlab:/home/gitlab
nobody:/nonexistent
.
.
```

Each line is a concatenation of a username, the colon character (:), and the home directory path for that username. Your script should output such a line for each user on the system.

**Script:**

```bash
#!/bin/bash

awk -F: '{print $1 ":" $6}' /etc/passwd
```

**Commands:**

```bash
chmod +x list_users_awk.sh
./list_users_awk.sh
```

### 2. Study the Git commit graph shown below. What sequence of Git commands could have resulted in this commit graph?

To answer this, based on the provided commit graph:

1. Start on the `main` branch and make the initial commit:
    ```bash
    git init gitlab_test
    git add file.txt
    git commit -m "first commit"
    git push	
    ```

2. Make a second commit on the `main` branch:
    ```bash
    git add file.txt
    git commit -m "second commit"
    git push	

    ```

3. Create a feature branch from the `main` branch:
    ```bash
    git checkout -b feature-branch
    ```

4. Make a commit on the `feature-branch`:
    ```bash
    git add feature.txt
    git commit -m "awesome feature"
    git push
    ```

5. Switch back to the `main` branch:
    ```bash
    git checkout main
    ```

6. Make a third commit on the `main` branch:
    ```bash
    git add file.txt
    git commit -m "third commit"
    git push
    ```


7. Merge the `feature-branch` into the `main` branch:
    ```bash
    git merge feature-branch
    git pull
    ```

8. Make a fourth commit on the `main` branch:
    ```bash
    git add file.txt
    git commit -m "fourth commit"
    git push
    ```

### 3. Write a brief blog post for GitLab that explains what Git is and what it can do for you.

**Blog Post:**

**What is Git and What Can It Do for You?**

Git is a powerful, distributed version control system designed to handle everything from small to very large projects with speed and efficiency. 
Created by Linus Torvalds in 2005, Git allows multiple developers to work on a project simultaneously without overwriting each other's changes. 
This capability is crucial for collaboration in software development.

**Key Features of Git:**

1. **Version Control:** Git tracks changes to files, allowing you to revert to previous states and understand the history of your project. This is invaluable for debugging and understanding the evolution of your codebase.

2. **Branching and Merging:** Git's branching model allows you to create separate branches for features, bug fixes, or experiments. You can work on these branches independently and merge them back into the main project when ready.

3. **Distributed System:** Every developer has a local copy of the entire project history, which means you can work offline and still have access to the full version history. Changes can be shared among team members by pushing and pulling from repositories.

4. **Collaboration:** Git supports multiple workflows, from centralized to distributed models. It integrates with platforms like GitLab, GitHub, and Bitbucket, providing tools for code review, issue tracking, and continuous integration.

**Benefits of Using Git:**

- **Collaboration:** Facilitate team collaboration with features like branches and pull requests.
- **History Tracking:** Keep a detailed history of changes to improve transparency and accountability.
- **Flexibility:** Adapt to various workflows, whether you're working solo or with a large team.
- **Efficiency:** Manage large projects efficiently with Git's performance-optimized architecture.

Whether you're a solo developer or part of a large team, Git provides the tools and workflows needed to manage your projects effectively.

### 4. Tell us about a recent issue you debugged or a problem you solved. How did you go about debugging it? What tools did you use? What was the outcome?

**Debugging a Performance Issue in a Web Application**

Recently, I encountered a performance issue in a web application where page load times had significantly increased. Here's how I approached the problem:

1. **Identification:** The issue was identified through user reports and monitoring tools (New Relic) that showed increased response times and server load.

2. **Reproduction:** I attempted to reproduce the issue in a development environment. I noted the specific conditions under which the performance degradation occurred, which helped narrow down the potential causes.

3. **Diagnosis:** Using a combination of tools like `top`, `htop`, and `strace` on the server, I analyzed the resource usage and system calls. I also used the browser's developer tools to profile the front-end performance.

4. **Root Cause Analysis:** The profiling revealed that a specific API endpoint was taking an unusually long time to respond. Further inspection of the backend logs and database queries showed that a recent change had introduced a non-indexed query that was causing a full table scan.

5. **Solution:** I added the necessary indexes to the database, optimized the query, and implemented caching for frequently requested data.

6. **Testing:** After making these changes, I tested the application in a staging environment to ensure that the performance issue was resolved without introducing new bugs.

7. **Deployment:** Once verified, the changes were deployed to production. Monitoring tools confirmed that the response times had returned to normal levels.

**Outcome:** The performance issue was resolved, leading to faster page load times and improved user satisfaction. The process also highlighted the importance of thorough testing and monitoring, leading to improved practices for future deployments.

### References:

- Bash Scripting: [GNU Bash Manual](https://www.gnu.org/software/bash/manual/bash.html)
- `awk` Command: [GNU Awk User's Guide](https://www.gnu.org/software/gawk/manual/gawk.html)
- Git Basics: [Pro Git Book](https://git-scm.com/book/en/v2)
- Debugging Tools: [New Relic Documentation](https://docs.newrelic.com/), [Linux Man Pages](https://man7.org/linux/man-pages/)
- Fine Tuning Content: Chatgpt.com. (2024). ChatGPT. [online] Available at: https://chatgpt.com/c/ce2dba44-39f5-40a0-b506-ffce486d54d0.
