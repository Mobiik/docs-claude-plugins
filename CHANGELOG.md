# Changelog

Todos los cambios notables a este repositorio se documentan aquí.

El formato sigue [Keep a Changelog 1.1.0](https://keepachangelog.com/en/1.1.0/) y este proyecto adhiere a [Semantic Versioning 2.0.0](https://semver.org/spec/v2.0.0.html).

> Esqueleto inicial generado por `Mobiik/.github/scripts/new-repo-init.yml`. El owner llena las versiones a partir del primer release.

---

## [Unreleased]

### Added
### Changed
### Deprecated
### Removed
### Fixed
### Security

---

## Convenciones

| Cambio | Bump SemVer |
|---|---|
| Breaking change en API pública | MAJOR (1.x.x → 2.0.0) |
| Nueva feature backward-compatible | MINOR (1.0.x → 1.1.0) |
| Bug fix backward-compatible | PATCH (1.0.0 → 1.0.1) |

## Procedimiento de release

```bash
# 1. Mergear cambios a main
# 2. Verificar que CI corre en verde (Quality Gates pipeline)
# 3. Bump en este CHANGELOG (mover [Unreleased] → [v1.X.Y])
# 4. Tag firmado
git tag -s v1.X.Y -m "Release v1.X.Y"
git push origin v1.X.Y

# 5. Anuncio en Slack/Teams según política del proyecto
```

---

[Unreleased]: https://github.com/{{ORG}}/{{REPO}}/compare/HEAD
