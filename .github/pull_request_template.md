## Summary
Describe the change and why it’s needed.

## Type of change
- [ ] Bug fix
- [ ] Feature
- [ ] Refactor/cleanup
- [ ] CI/docs
- [ ] Breaking change

## How verified
Commands run locally and results (paste key outputs):
```
./gradlew :app:assembleDebug :app:testDebugUnitTest :app:lintDebug :app:ktlintCheck :app:detekt
```

## Screenshots / Screen recording
If UI-affecting, include before/after.

## Checklist
- [ ] Unit tests added/updated where appropriate
- [ ] Lint/ktlint/detekt pass locally
- [ ] No secrets committed
- [ ] Docs updated (README/CHANGELOG/WARP.md) if needed
- [ ] Linked issues (Fixes #123)
