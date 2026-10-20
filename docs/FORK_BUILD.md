# HMCL Fork — Downloads and build credentials

This fork keeps Minecraft game and add-on download features available in mainland China, while preserving regional mirror selection. Launcher self-update checks against the upstream HMCL distribution are disabled: obtain fork builds from this repository's own Actions artifacts.

## GitHub Actions credentials

Under **Settings → Secrets and variables → Actions → Repository secrets**, you may configure:

- `MICROSOFT_AUTH_ID`: Microsoft Entra OAuth **Application (client) ID**, not an access token or client secret. Needed to enable Microsoft account sign-in in your build.
- `CURSEFORGE_API_KEY`: CurseForge API key. Needed for the CurseForge integration.

The Java CI workflow tolerates missing values (build defaults to empty strings), but the corresponding integrations may not work. An automatically provided `GITHUB_TOKEN` is used by GitHub Actions; no manually generated personal access token is required for normal CI.

The upstream release and mirror workflows have repository-owner guards. `CNB_SYNC_TOKEN` and `GITEE_SYNC_TOKEN` are not needed for this fork's normal builds. Add your own equivalent only if you deliberately set up releases or mirrors to accounts under your control.

Use `./gradlew build --no-daemon --parallel` locally or GitHub Actions **Java CI** to produce builds. These changes do not disable Minecraft, loader, or mod update checks.
