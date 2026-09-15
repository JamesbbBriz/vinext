# Respect project .gitignore during compatibility scans

The compatibility scanner excludes project-local ignored source and generated files,
including nested .gitignore files and negations. Default toolchain exclusions remain
unconditional. This affects check reports only, not route discovery or builds.

Use `ignore` (already present in the lockfile) as a direct CLI dependency rather
than implementing Git pattern syntax or requiring a Git executable/repository.
Rules are scoped to the supplied project root; ancestor/global Git ignore files
and the Git index are intentionally not consulted, so standalone project copies
produce the same report. No network, storage migration, or public API change.
