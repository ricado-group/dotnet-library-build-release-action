# .NET Library Build and Release Action
A Composite Action that Builds, Publishes and Releases a .NET 6 Library

## Inputs

### `project-name`

**Required** The Project Name (e.g. RICADO.Logging)

### `private-nuget-url`

**Required** The URL of the Private NuGet Repository (e.g. https://nuget.pkg.github.com/myname/index.json)

### `private-nuget-token`

**Required** The Token used for Authentication with the Private NuGet Repository

### `public-nuget-url`

_Optional_ The URL of the Public NuGet Repository (e.g. https://api.nuget.org/v3/index.json)

Defaults to `https://api.nuget.org/v3/index.json`

### `public-nuget-token`

_Optional_ The Token used for Authentication with the Public NuGet Repository

### `publish-public`

_Optional_ Whether the Library should be Published to the Public NuGet Repository

Defaults to `false`

## Example Usage

```yml
uses: ricado-group/dotnet-library-build-release-action@v1.1
with:
  project-name: 'RICADO.Logging'
  private-nuget-url: 'https://nuget.pkg.github.com/myname/index.json'
  private-nuget-token: ${{ secrets.GITHUB_ACCESS_TOKEN }}
  public-nuget-token: ${{ secrets.NUGET_TOKEN }}
  publish-public: true
```