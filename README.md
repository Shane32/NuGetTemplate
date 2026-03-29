# NuGetTemplate

A template repository for creating NuGet packages with GitHub Actions CI/CD, SourceLink support, and best-practice MSBuild configuration.

## Getting Started

Follow these steps after creating a new repository from this template:

### 1. Rename the solution and project files

Rename `NuGetTemplate.slnx` and `Project/Project.csproj` to match your package name, and update the solution file to reference the renamed project. For example, for a package named `MyCompany.MyLibrary`:

- `NuGetTemplate.slnx` → `MyCompany.MyLibrary.slnx`
- `Project/Project.csproj` → `Project/MyCompany.MyLibrary.csproj`

The `.csproj` filename determines the default NuGet package ID, so it must match the desired package name. Also update the `ProjectReference` in `Tests/Tests.csproj` to point to the renamed file.

### 2. Update `Directory.Build.props`

Edit [`Directory.Build.props`](Directory.Build.props) to set your package metadata:

```xml
<Copyright>Your Name</Copyright>
<Authors>Your Name</Authors>
<!-- Optional: add a logo image to the repo root and reference it here -->
<!-- <PackageIcon>logo.png</PackageIcon> -->
```

### 3. Update `LICENSE.txt`

Update [`LICENSE.txt`](LICENSE.txt) with your name and the current year. If you change the license type, also update the `PackageLicenseExpression` property in [`Directory.Build.props`](Directory.Build.props) to match (e.g. `MIT`, `Apache-2.0`). See [SPDX license identifiers](https://spdx.org/licenses/) for valid values.

### 4. Configure GitHub Actions secrets

todo

### 5. Update this README

Replace this file with documentation for your package.

## Template Notes

- **`IsPackable`** defaults to `false` for all projects. The main `Project/` project has it set to `true`. When adding a second project that should produce a NuGet package, add `<IsPackable>true</IsPackable>` to that project file. Test projects and other non-package projects should leave it as `false` (the default).

- **SourceLink** is automatically configured for all packable projects via `Microsoft.SourceLink.GitHub`. Ensure the repository is hosted on GitHub for this to work correctly.

- **`LICENSE.txt`**, **`README.md`**, and the logo image (when `PackageIcon` is set in `Directory.Build.props`) from the repository root are automatically included in all NuGet packages produced by packable projects.

- **`ContinuousIntegrationBuild`** is enabled automatically when running in GitHub Actions, which ensures deterministic builds and correct SourceLink paths.

## License

This template is licensed under the [MIT License](LICENSE.txt).
