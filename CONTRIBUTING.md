# Contributing to Docker PHP Development Environment

First off, thank you for considering contributing to this Docker PHP development environment! It's people like you that make it a great tool for everyone.

## Code of Conduct

This project and everyone participating in it is governed by our Code of Conduct. By participating, you are expected to uphold this code.

## How Can I Contribute?

### Reporting Bugs

Before creating bug reports, please check the issue list as you might find out that you don't need to create one. When you are creating a bug report, please include as many details as possible:

* **Use a clear and descriptive title**
* **Describe the exact steps to reproduce the problem**
* **Provide specific examples** (Docker and host OS versions, commands used)
* **Describe the behavior you observed and what behavior you expected**
* **Include logs** (Docker logs, Apache/PHP logs if relevant)

### Suggesting Enhancements

Enhancement suggestions are tracked as GitHub issues. When creating an enhancement suggestion, please include:

* **Use a clear and descriptive title**
* **Provide a step-by-step description of the suggested enhancement**
* **Provide specific examples of how the enhancement would work**
* **Explain why this enhancement would be useful**

### Pull Requests

1. Fork the repo and create your branch from `main`
2. If you've added code that should be tested, add tests
3. If you've changed configurations, update the documentation
4. Ensure all tests pass
5. Make sure your code follows the existing style

## Development Process

### Setting Up Development Environment

1. Fork the repository
2. Clone your fork:
   ```bash
   git clone https://github.com/mtm-heinhtetsoe/docker-php-dev.git
   cd docker-php-dev
   ```
3. Create a branch:
   ```bash
   git checkout -b feature/my-new-feature
   ```

### Making Changes

#### Docker Configuration Changes

1. Document any changes to environment variables in README.md
2. Test changes with different PHP applications
3. Verify all services start correctly
4. Check logs for any errors
5. Update documentation if needed

#### Documentation Changes

1. Keep README.md up to date with all changes
2. Use clear and consistent formatting
3. Add examples where appropriate
4. Verify all commands and paths

### Commit Guidelines

* Use clear and meaningful commit messages
* Reference issues and pull requests in commit messages
* Keep commits focused and atomic

Example commit message:
```
Add PHP Redis extension support

- Add php8.2-redis package to Dockerfile
- Update documentation with Redis configuration
- Add example Redis configuration
```

### Testing

Before submitting a pull request:

1. Test building the containers:
   ```bash
   docker-compose build
   ```

2. Test starting the environment:
   ```bash
   docker-compose up -d
   ```

3. Verify all services are running:
   ```bash
   docker-compose ps
   ```

4. Check logs for errors:
   ```bash
   docker-compose logs
   ```

5. Test with a sample PHP application

### Documentation Style

* Use Markdown formatting
* Keep line length reasonable (around 80 characters)
* Use code blocks for commands and configuration examples
* Include comments in configuration files
* Use relative links when linking to other files in the repository

## Style Guides

### Git Commit Messages

* Use the present tense ("Add feature" not "Added feature")
* Use the imperative mood ("Move cursor to..." not "Moves cursor to...")
* Limit the first line to 72 characters or less
* Reference issues and pull requests liberally after the first line

### Dockerfile Style

* Use official base images
* Sort multi-line arguments alphanumerically
* Use appropriate continuation line alignment
* Include comments for non-obvious operations
* Use environment variables for configurable values

### Configuration Files

* Include comments explaining non-standard settings
* Use consistent indentation
* Group related settings together
* Document security-sensitive settings

## Additional Notes

### Issue and Pull Request Labels

* `bug` - Something isn't working
* `enhancement` - New feature or request
* `documentation` - Documentation only changes
* `security` - Security related changes
* `performance` - Performance improvements
* `maintenance` - Repository maintenance
* `docker` - Docker configuration changes
* `testing` - Testing related changes

## Recognition

Contributors who have their PRs merged will be added to the README.md contributors section.

Thank you for contributing!
