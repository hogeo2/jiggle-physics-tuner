![Jiggle Physics Tuner](https://github.com/user-attachments/assets/2da1610c-1a0c-42a7-9e5c-d9a292a293d6)

# Jiggle Physics Tuner

A free tool for **Monster Hunter Wilds** that lets you interactively tune the bust (chest) physics on a Ver.R-based armor mod — how strongly it jiggles and how far it can swing — with sliders, instead of hand-editing raw physics files.

🧪 **This is an early test release.** It's been verified on real mod files during development, but hasn't had much outside testing yet. Bug reports are very welcome — see Support below.

🆓 **Free forever.** No paywall, no locked tiers, no catch.

## What it does

- Point it at a single already-extracted `chain2` file (the one carrying the Body part's bust physics)
- Move the sliders (damping, spring force, swing angle limits), click Apply, check the result in-game, then come back and adjust again
- Re-running on the same file with different values is safe and expected — the tool only backs up the file's *original* data once, the very first time it's ever touched
- Picking a file that's already been adjusted automatically loads the values currently stored in it, instead of resetting to defaults

⚠️ **Ver.R-based Body parts only.** This tool detects physics bones using the `L_Bust_CH` / `R_Bust_CH` naming convention that Ver.R-style releases use. Point it at a chain2 file from a different mod format and it will simply find no bust physics to adjust and change nothing.

## Before you start

This tool assumes you already have a working modding setup:

- **Blender 4.5**, with [RE-Mesh-Editor](https://github.com/NSACloud/RE-Mesh-Editor) and [RE-Chain-Editor](https://github.com/NSACloud/RE-Chain-Editor) installed and enabled

That's it — unlike some other tools built the same way, this one doesn't need Monster Hunter Wilds' extracted game data, 7-Zip, or WinRAR. It only edits a chain2 physics file already inside an unpacked mod folder.

Full setup and usage instructions are included in **How to Use.html** inside the download.

⚠️ Because of this environment requirement, support for individual setup issues is limited — please make sure your Blender/RE-tools environment is working correctly before reaching out. For questions or bugs, please use [GitHub Issues](../../issues) rather than DMs.

If Blender crashes or the log stops partway through, just click **Apply** again — this can happen occasionally. It's safe to retry: nothing is left half-written, since Blender only overwrites the file once the whole adjustment finishes successfully.

If the crash report specifically mentions a background thread and `EXCEPTION_ACCESS_VIOLATION`, this has been traced (at least once, in a related tool) to an unrelated third-party Blender add-on, **Cats Blender Plugin**, running its own delayed background timer even in headless mode. This tool doesn't use Cats Blender Plugin at all. If you have it installed, try disabling it (Blender's `Edit > Preferences > Add-ons`, search "Cats") or temporarily moving aside `%APPDATA%\Blender Foundation\Blender\<version>\extensions\user_default\cats_blender_plugin`, then re-run.

## Download

Grab the latest release from the [Releases page](../../releases/latest) — it's a single zip containing the tool, the usage guide, and license notices.

Only the compiled `.exe` is distributed here; this repository does not include the tool's source.

## Please respect mod authors

This tool changes physics values inside someone else's armor mod for **your own personal use**. Redistributing someone else's mod — adjusted or not — without the original author's permission is not okay. If you share an adjusted mod, keep it to yourself or ask the original author first.

## Support

If this tool saved you time, a coffee is always appreciated — but it's free forever either way. 🙏
[ko-fi.com/pogeo](https://ko-fi.com/pogeo)

## Verifying your download

Each release's notes include a SHA-256 checksum for the release zip. To verify the file you downloaded matches:

```powershell
Get-FileHash "JigglePhysicsTuner-v0.1.0.zip" -Algorithm SHA256
```

## Disclaimer

This tool is distributed as a compiled `.exe`. Only download it from this repository's [Releases page](../../releases/latest), and verify the SHA-256 checksum before running it. Beyond that, it's provided as-is, with no warranty — use it at your own risk. The author isn't responsible for pre-existing issues on your device (a system that was already compromised, infected, or misconfigured before running this tool), for anything your own antivirus/security software should be handling, or for any damage to your mods, save data, or game installation.

This tool doesn't request admin rights, doesn't touch anything outside the chain2 file you choose and its own settings file, and doesn't connect to the network except when you click the Ko-fi link yourself. It rewrites the chain2 file you point it at in place (after backing up the original data the first time), so mistakes are possible: keep a backup of your Mods folder, and test an adjusted result in-game before assuming it's correct.
