# My typical CI setup

* Install nbgv as local tool.
  * I also use `dotnet-ef` as local tool to prevent any version compatibility issues.

* Usually git commit based build number (git version default - only major/minor specified)
  * Somtimes `"version": "2.0.0-preview.{height}",` for experimental public packages

## Azure Pipelines

```yaml
- script: |
    dotnet tool restore
    dotnet nbgv cloud -a
displayName: 'Update build number based on git version'
```

## Github Actions

```yaml
- name: 'Calculate version numbers'
    uses: dotnet/nbgv@master
    with:
      setAllVars: true
```
