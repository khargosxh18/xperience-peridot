Changelog: Peridot (20/06/2026)

Device CL:
Graphics and Performance:-

Switched to Vulkan for graphics rendering.
Enabled 120 FPS support for the Screen Recorder.
Enabled frame pacing for smoother visuals.
Configured Dexopt optimizations.
Imported Expensive Rendering Hints, thanks to ahmad and shikhar.
Refined interaction and scheduler parameters.
Optimized and adjusted interaction hints, including adding UclampFGMin>18.
Refined Powerhint configurations.
Disabled Skia tracing by default.

System and Framework:-

Implemented HintManager for HWUI, which was subsequently reverted.
Implemented ChargeControl Qs Service and performed associated refactoring.
Added a gaming mode profile to PowerProfileTileService.
Moved node permissions to sys.boot_completed for optimization.
Nuked redundant LineageOS dependencies.

Camera and Hardware:-

Included MiuiCamera.
Configured camera properties for XPE.
Dropped FM HAL.
Debloated camera2.

Debugging and Cleanup:-

Dropped unnecessary performance tuning from the root directory.
Dropped config power decouple mode.
Dropped the duplicate gamebar.
Resolved SELinux policy denials, specifically for Diag-router and bring-up.
Disabled htsr on profile toggle.
Disabled ART debug settings.
Disabled some Wlan debugs.
Included an application debloater.

Kernel Cl:
Added DroidSpace Support.
