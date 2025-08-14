# Claude (Code) Course Assistant Template

A GitHub template repository for instructors to utilize Claude Code for course management.

## Overview

This template provides a structured framework for instructors to leverage Claude as a course development assistant. By customizing the included `CLAUDE.md` file with your course-specific information, you can create a consistent, intelligent assistant that helps develop course materials, assignments, and assessments aligned with your pedagogical goals.

## Features

- **Structured Course Development**: Pre-configured guidelines for creating lesson materials, assignments, and assessments
- **Consistency Enforcement**: Claude will maintain consistency across all course materials
- **Pedagogical Best Practices**: Built-in emphasis on scaffolding, clarity, and appropriate academic rigor
- **Flexible Framework**: Adaptable to any course, programming language, or academic level
- **Quality Assurance**: Integrated checklists and standards for course material development
- **Multi-Project Container Orchestration**: send docker commands to the host socker within this container

## Getting Started

### 1. Use This Template

Click the "Use this template" button on GitHub to create a new repository based on this template.

### 2. Customize CLAUDE.md

Edit the `CLAUDE.md` file to include your course-specific information:

1. Replace all bracketed placeholders (e.g., `[COURSE CODE]`, `[INSTRUCTOR NAME]`) with your actual information
2. Update the repository structure section to match your intended organization
3. Modify learning objectives to align with your course goals
4. Specify your preferred programming languages and tools
5. Adjust the semester schedule and topic sequencing
6. Add any course-specific guidelines or requirements

### 3. Set Up Your Development Environment

Open this repository as a devContainer:

1. Ensure you have Docker installed on your system
2. Open the repository in VS Code
3. When prompted, select "Reopen in Container" (or use the Command Palette: "Dev Containers: Reopen in Container")
4. The devContainer will automatically set up the development environment with all necessary tools
5. Claude will automatically recognize and use the `CLAUDE.md` file as context for all interactions

### 4. Develop Your Course Materials

With Claude configured, you can now:

- **Create Lesson Materials**: "Help me create a lesson on [TOPIC] following our course structure"
- **Design Assignments**: "Create a programming assignment for [CONCEPT] with starter code and test cases"
- **Generate Practice Problems**: "Generate 8 practice problems with solutions for [TOPIC]"
- **Build Assessments**: "Create exam questions testing understanding of [LEARNING OBJECTIVE]"
- **Review and Refine**: "Review this material and suggest improvements for clarity and consistency"
- **Multi-Project Management with Docker-out-of-Docker**: "Test the first programming assignment container to confirm the tests pass"

## Repository Structure

After customization, your repository might look like:

```
your-course-repo/
├── .devcontainer/          # Development container configuration
├── CLAUDE.md               # Course-specific instructions for Claude
├── README.md               # Course overview and syllabus
├── lessons/                # Lesson materials
│   ├── week01/
│   ├── week02/
│   └── ...
├── assignments/            # Programming and written assignments
│   ├── pa01/
│   ├── pa02/
│   └── ...
├── exams/                  # Exam materials and reviews
└── resources/              # Additional resources
```

## Best Practices

1. **Keep CLAUDE.md Updated**: As your course evolves, update the instructions to reflect changes
2. **Version Control**: Commit changes regularly to track course development progress
3. **Iterative Development**: Start with core materials and progressively add detail
