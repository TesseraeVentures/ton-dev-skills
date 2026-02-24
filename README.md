# TON Dev Skills

Practical TON contract tooling for agents and developers.

## Install

```bash
npm i -g @tesserae/ton-dev-skills
# or run without install
npx -y @tesserae/ton-dev-skills doctor --json
```

## 60-second judge path

```bash
npx -y @tesserae/ton-dev-skills doctor --json
npx -y @tesserae/ton-dev-skills demo --pass --ci --out ./.ton-dev-artifacts
cat ./.ton-dev-artifacts/demo-summary.json
```

## Commands

- `ton-dev doctor [--json]`
- `ton-dev init [dir]`
- `ton-dev demo [--json] [--ci] [--pass|--fail] [--out <dir>]`
- `ton-dev audit <file|dir> [--format table|json|sarif] [--out <file>] [--explain]`
- `ton-dev rules --ton`
- `ton-dev scorecard [--json]`

## Why this helps evaluators fast

- Deterministic CI demo output (`CI_RESULT=...` + JSON + SARIF)
- TON-native security checks (bounce/replay/auth/gas/send-mode focus)
- Machine-readable outputs for automation and screenshots

## Quick examples

```bash
# Safe pass-mode demo
npx -y @tesserae/ton-dev-skills demo --pass --ci --out ./.ton-dev-artifacts

# Finding-mode demo
npx -y @tesserae/ton-dev-skills demo --fail --ci --out ./.ton-dev-artifacts

# Explain findings in table mode
npx -y @tesserae/ton-dev-skills audit examples/jetton.fc --format table --explain

# Emit SARIF file
npx -y @tesserae/ton-dev-skills audit examples/jetton.fc --format sarif --out report.sarif
```

## Links

- npm: https://www.npmjs.com/package/@tesserae/ton-dev-skills
- GitHub: https://github.com/TesseraeVentures/ton-dev-skills

## License

MIT
