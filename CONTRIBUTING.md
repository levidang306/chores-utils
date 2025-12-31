# Contributing to chores-utils

Thank you for your interest in contributing to chores-utils! We welcome contributions from everyone.

## How to Contribute

### Reporting Bugs

If you find a bug, please open an issue on GitHub with:
- A clear title and description
- Steps to reproduce the issue
- Expected vs actual behavior
- Your environment (Node version, OS, etc.)

### Suggesting Features

We love new ideas! Please open an issue with:
- A clear description of the feature
- Use cases and examples
- Why it would be useful

### Pull Requests

1. **Fork the repository**
2. **Create a branch** for your feature:
   ```bash
   git checkout -b feature/amazing-feature
   ```

3. **Make your changes**:
   - Write clear, readable code
   - Follow existing code style
   - Add JSDoc comments for new functions
   - Update README.md if needed

4. **Test your changes**:
   ```bash
   npm run build
   ```

5. **Commit your changes**:
   ```bash
   git commit -m "Add amazing feature"
   ```

6. **Push to your fork**:
   ```bash
   git push origin feature/amazing-feature
   ```

7. **Open a Pull Request** on GitHub

## Development Setup

```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/chores-utils.git
cd chores-utils

# Install dependencies
npm install

# Build the project
npm run build
```

## Code Style

- Use TypeScript
- Follow existing patterns
- Write descriptive function names
- Add JSDoc comments
- Keep functions small and focused

## Adding New Utilities

When adding new utility functions:

1. Choose the appropriate file (string.ts, array.ts, etc.)
2. Add the function with JSDoc comments
3. Export it from the module
4. Update README.md with documentation
5. Include usage examples

Example:
```typescript
/**
 * Reverses a string
 */
export function reverse(str: string): string {
  return str.split('').reverse().join('');
}
```

## Questions?

Feel free to open an issue or reach out to the maintainers.

Thank you for contributing! 🎉
