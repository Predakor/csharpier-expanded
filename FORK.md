# csharpier-expanded

[CSharpier](https://github.com/belav/csharpier) with a few opinionated changes for the HikeIt project. Everything else is upstream, so see the upstream README for usage.

Base: upstream `1.0.1`. Fork versions are `<upstream version>.<revision>`, for example `1.0.1.1`. The package ID and command stay `CSharpier` / `csharpier` so editors and tools find it.

## Changes from upstream

- **Member chains.** A chain with two or more calls always breaks, one call per line, with the receiver on its own line. Upstream keeps every chain on one line when it fits the print width. Implemented in `Src/CSharpier.Core/CSharp/SyntaxPrinter/SyntaxNodePrinters/InvocationExpression.cs`.

## Building a package

```
dotnet pack Src/CSharpier.Cli -c Release -p:Version=<version> -p:NuGetAudit=false -p:TreatWarningsAsErrors=false -o nupkg
```

`NuGetAudit` is off because a build-time-only dependency (Scriban, in the source generators) has advisories that upstream's settings treat as errors.

Publish the resulting `CSharpier.<version>.nupkg` as a GitHub Release asset.
