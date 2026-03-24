# Contributing to Flavor

Thank you for your interest in contributing to Flavor! Here are some guidelines to help you get started.

## How to Contribute

### Reporting Bugs

- Open an [issue](https://github.com/nakamura196/hugo-theme-flavor/issues) with a clear description
- Include screenshots if the issue is visual
- Specify your Hugo version, browser, and OS

### Suggesting Features

- Open an [issue](https://github.com/nakamura196/hugo-theme-flavor/issues) with the "enhancement" label
- Describe the use case and expected behavior

### Pull Requests

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/my-feature`)
3. Test your changes with the exampleSite:
   ```bash
   cd exampleSite
   npm install
   npm run dev
   ```
4. Commit your changes (`git commit -m 'Add my feature'`)
5. Push to your branch (`git push origin feature/my-feature`)
6. Open a Pull Request

### Development Setup

```bash
git clone https://github.com/nakamura196/hugo-theme-flavor.git
cd hugo-theme-flavor/exampleSite
npm install
npm run dev
```

### Code Style

- Use 2-space indentation in HTML templates
- Follow Hugo template conventions
- CSS changes go in `assets/css/main.css` within the appropriate `@layer`
- Add i18n keys for any user-facing strings (in both `i18n/en.yaml` and `i18n/ja.yaml` at minimum)

### Adding Translations

To add a new language:

1. Copy `i18n/en.yaml` to `i18n/{lang}.yaml`
2. Translate all string values
3. Submit a Pull Request

## License

By contributing, you agree that your contributions will be licensed under the MIT License.
