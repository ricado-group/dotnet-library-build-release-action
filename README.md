# .NET Library Build and Release Action
A Composite Action that Builds, Publishes and Releases a .NET 7+ Library

## Inputs

### `project-name`

**Required** The Project Name (e.g. RICADO.Logging)

### `github-token`

**Required** The GitHub Token used to Generate a Changelog and Create Releases

### `private-nuget-url`

**Required** The URL of the Private NuGet Repository (e.g. https://nuget.pkg.github.com/myname/index.json)

### `private-nuget-token`

**Required** The Token used for Authentication with the Private NuGet Repository

### `public-nuget-url`

_Optional_ The URL of the Public NuGet Repository (e.g. https://api.nuget.org/v3/index.json)

Defaults to `https://api.nuget.org/v3/index.json`

### `public-nuget-user`

_Optional_ The Username (Profile Name) of the NuGet.org Account used for Trusted Publishing with the Public NuGet Repository

### `publish-public`

_Optional_ Whether the Library should be Published to the Public NuGet Repository

Defaults to `false`

### `dotnet-version`

_Optional_ The .NET SDK Version to be used for Builds (e.g. 7.0.x)

Defaults to `7.0.x`

## Outputs

### `changelog`

A Markdown formatted changelog

## Example Usage

```yml
permissions:
  id-token: write # Required if Publishing to NuGet
  contents: write

jobs:
  build-and-release:
    permissions:
      id-token: write # Required if Publishing to NuGet
      contents: write
    
    steps:
      # Checkout Code
      - name: Checkout
        uses: actions/checkout@v6
      
      # Build and Release
      - name: Build and Release
        uses: ricado-group/dotnet-library-build-release-action@v2
        with:
          project-name: 'RICADO.Logging'
          github-token: ${{ secrets.GITHUB_TOKEN }}
          private-nuget-url: 'https://nuget.pkg.github.com/myname/index.json'
          private-nuget-token: ${{ secrets.PERSONAL_ACCESS_TOKEN }}
          public-nuget-user: ${{ vars.NUGET_USER }}
          publish-public: true
          dotnet-version: 7.0.x
```

## Stay Updated with Dependabot

Use [Dependabot](https://docs.github.com/en/github/administering-a-repository/keeping-your-actions-up-to-date-with-github-dependabot) to update your GitHub Actions by creating a `.github/dependabot.yml` file:

```yaml
version: 2
updates:
  # Maintain Dependencies for GitHub Actions
  - package-ecosystem: "github-actions"
    directory: "/"
    schedule:
      interval: "daily"
```