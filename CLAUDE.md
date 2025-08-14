# Course Assistant Instructions Template

## Important Instructions for Claude

This repository contains course materials currently in development. Your role as the Course Assistant is to help the instructor develop, refine, and organize course content. When assisting with course development:

1. Prioritize pedagogical clarity and scaffolding of complex concepts
2. Ensure consistency across all course materials and assignments
3. Reference existing materials in the repository when creating new content
4. Consider the course schedule and pacing when developing materials
5. Maintain academic rigor appropriate for the course level

## Course Overview

<!-- Fill in the following information for your specific course -->

- **Course**: [COURSE CODE - Course Name]
- **Semester**: [SEMESTER YEAR]
- **Instructor**: [INSTRUCTOR NAME]
- **Prerequisites**: [LIST PREREQUISITES]
- **Meeting Times**: [DAYS/TIMES]
- **Office Hours**: [DAYS/TIMES/LOCATION]

## Repository Structure

<!-- Describe your repository organization. Example structure: -->

- `/module1/` - [Description of module 1 content]
- `/module2/` - [Description of module 2 content]
- `/assignments/` - [Programming assignments or homework]
- `/exams/` - [Exam materials and review content]
- `/resources/` - [Additional resources and references]

## Key Development Tasks

<!-- List the primary tasks for course development. Examples: -->

1. Create comprehensive lesson materials for each topic
2. Develop programming assignments with starter code and test cases
3. Design practice problems and solutions
4. Create exam review materials
5. Develop grading rubrics

## Course Learning Objectives

<!-- List your course learning objectives. Students completing this course should be able to: -->

1. [Learning objective 1]
2. [Learning objective 2]
3. [Learning objective 3]
4. [Add more as needed]

### DevContainer Command Execution

This repository uses devContainers for consistent development environments. This project's devcontainer is configured with Docker-out-of-Docker to control other containers running on the host.

**Outside Container Control:**

**Finding Active Containers:**

```bash
# List all running containers to identify project containers
docker ps
```

**Project-Specific DevContainer Configuration Discovery:**

Different submodules may have different devContainer setups. Always check each project's configuration before executing commands:

**Checking User and Environment Setup:**

```bash
# Check what user the container is configured for
docker exec CONTAINER_ID whoami

# Check available users in the container
docker exec CONTAINER_ID cat /etc/passwd | grep -E "(vscode|node|root)"

# Look for virtual environment paths
docker exec CONTAINER_ID find /home -name "activate" 2>/dev/null
docker exec CONTAINER_ID find /opt -name "activate" 2>/dev/null

# Check working directory setup
docker exec CONTAINER_ID pwd
docker exec CONTAINER_ID ls -la /workspace 2>/dev/null || docker exec CONTAINER_ID ls -la /workspaces 2>/dev/null
```

**Inspecting DevContainer Configuration:**

```bash
cat .devcontainer/Dockerfile
cat .devcontainer/devcontainer.json
```

**Container Management Best Practices:**

1. **Identify Active Containers**: Always run `docker ps` first to see what's currently running
2. **Project-Specific Commands**: Use appropriate commands for each project type
3. **Environment Activation**: Activate virtual environments when required
4. **Working Directory**: Ensure you're in the correct working directory (`/workspace`)

**Troubleshooting Multiple Containers:**

- **Container Not Found**: Container may have been stopped/restarted, check `docker ps` again
- **Permission Issues**: Ensure correct user with `-u USERNAME` (check with `whoami`)
- **Command Not Found**: May need to activate virtual environment or install dependencies
- **Wrong Directory**: Make sure to `cd` to correct working directory (`/workspace` or `/workspaces`)
- **User Mismatch**: Check devContainer Dockerfile for correct `USER` directive
- **Different Base Image**: Submodules may use different base images with different tool installations

**Important Notes:**

- Container IDs change when devContainers are rebuilt
- Each project (main + submodules) may have different development setups
- Always verify which container you're targeting before executing commands
