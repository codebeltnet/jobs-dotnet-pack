# Reusable Workflows for .NET CLI Pack

This repository contains reusable workflows for interacting with .NET CLI `pack` command in your CI/CD pipeline.

> These workflows is part of the Codebelt umbrella and ensures a consistent way of: 
> 
> - Defining your CI/CD pipeline 
> - Structuring your repository
> - Keeping your codebase small and feasible
> - Writing clean and maintainable code
> - Deploying your code to different environments
> - Automating as much as possible
>
> A paved path to excel as a DevSecOps Engineer.

## Available Workflows

- [default.yml](.github/workflows/default.yml) - the `dotnet pack` workflow that:
  - [installs the .NET SDK](https://github.com/codebeltnet/install-dotnet),
  - conditionally restores cached content,
  - downloads build artifacts,
  - sets the version of the NuGet package,
  - [packages previously built projects into NuGet packages](https://github.com/codebeltnet/dotnet-pack),
  - uploads the generated NuGet package as a workflow artifact.

### Usage

To call this workflow in your GitHub repository, you can follow these steps:

```yaml
pack-call:
    uses: codebeltnet/jobs-dotnet-pack/.github/workflows/default.yml@v2
```

#### Inputs

```yaml
with:
  # The version of your NuGet package, e.g., 1.0.0.
  version:
  # Optional path to the project(s) file to build. Supports globbing. Default is an empty string.
  projects: ''
  # Defines the build configuration. Default is Debug.
  configuration: 'Debug'
    # When set to true, includes preview versions of .NET. Default is false.
  include-preview: false
  # Sets the verbosity level of the command. Allowed values are quiet, minimal, normal, detailed, and diagnostic. Default is quiet.
  verbosity-level: 'quiet'
  # The pattern to download the build artifacts. Default, when left empty, is 'format('*-{0}', inputs.configuration)'.
  download-build-artifact-pattern: ''
  # The name of the NuGet package to upload. Default, when left empty, is 'format('NuGet-{0}', inputs.configuration)'.
  upload-packed-artifact-name: ''
  # When set, the current workspace will be overwritten with the content of the restore cache. Default is an empty string.
  restore-cache-key: ''
  # The maximum time in minutes to allow the job to run. Default is 15 minutes.
  timeout-minutes: 15
```

#### Secrets

This workflow has no secrets.

#### Outputs

This workflow has no outputs.

#### Example

```yaml
jobs:
  build:
    uses: codebeltnet/jobs-dotnet-pack/.github/workflows/default@v2
    with:
      configuration: Release
      version: 1.0.0
```

## Caller workflows to showcase the Codebelt experience

### Basic CI/CD Pipeline

- Bootstrapper API - https://github.com/codebeltnet/bootstrapper/blob/main/.github/workflows/pipelines.yml
- Extensions for Asp.Versioning API - https://github.com/codebeltnet/asp-versioning/blob/main/.github/workflows/pipelines.yml
- Extensions for AWS Signature Version 4 API - https://github.com/codebeltnet/aws-signature-v4/blob/main/.github/workflows/pipelines.yml
- Extensions for Globalization API - https://github.com/codebeltnet/globalization/blob/main/.github/workflows/pipelines.yml
- Extensions for Newtonsoft.Json API - https://github.com/codebeltnet/newtonsoft-json/blob/main/.github/workflows/pipelines.yml
- Extensions for Swashbuckle.AspNetCore API - https://github.com/codebeltnet/swashbuckle-aspnetcore/blob/main/.github/workflows/pipelines.yml
- Extensions for xUnit API - https://github.com/codebeltnet/xunit/blob/main/.github/workflows/pipelines.yml
- Extensions for YamlDotNet API - https://github.com/codebeltnet/yamldotnet/blob/main/.github/workflows/pipelines.yml
- Shared Kernel API - https://github.com/codebeltnet/shared-kernel/blob/main/.github/workflows/pipelines.yml
- Unitify API - https://github.com/codebeltnet/unitify/blob/main/.github/workflows/pipelines.yml

### Intermediate CI/CD Pipeline

- Savvy I/O - https://github.com/codebeltnet/savvyio/blob/main/.github/workflows/pipelines.yml

### Advanced CI/CD Pipeline

- Cuemon for .NET - https://github.com/gimlichael/Cuemon/blob/main/.github/workflows/pipelines.yml

## Contributing to Reusable Workflows for .NET CLI Pack

Contributions are welcome! 
Feel free to submit issues, feature requests, or pull requests to help improve these workflows.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
