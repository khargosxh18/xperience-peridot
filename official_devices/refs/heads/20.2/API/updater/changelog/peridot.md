ChangeLog: Peridot (17/09/2026

## Device
1.  Synced With Initial A17 Xperience-21 Source 
2.  Updated firmware/vendor blobs to OS3.0.303.0.WNPMIXM
3.  Added Bypass Charging Toggle And Support
4.  Added Pretuned ViPER4AndroidFX along the stock dolby curve
5.  More misc Changes
6.  Enabled ADPF CPU hints for smoother UI performance
7.  Enabled full ART optimizations using VDEX/ODEX for faster app execution
8.  Reverted the earlier power-decouple-mode overlay change
9.  Fixed the Touch Sampling QS tile's long-press not opening its settings screen
10.  XiaomiParts rework: added launcher option in the app drawer
11.  XiaomiParts rework: added a dedicated Charge Control settings screen
12.  XiaomiParts rework: added a dedicated PowerProfile Control settings screen
13. XiaomiParts rework: added separate notification and icon for Gaming Profile
14. Fixed SELinux policy blocking access to the persist fingerprint directory
15. Replaced the vendor_sysfs_usb_c sepolicy type with sysfs_typec
16. Added libion dependency required by the ANC HAL
17. Added Soong namespaces for NXP KeyMint3 and Weaver HALs
18. Reverted to the legacy libion implementation for stability
19. Enabled DEX pre-opt configuration by default
20. Reverted the xiaomi touch AIDL build change
21. Labeled additional Xiaomi touch sysfs nodes for SELinux
22. Set touch_filters and related nodes to 0666 permissions
23. Removed the unused sample qseecom client binary
24. Added a dummy keylayout for uinput-xiaomi
25. Added NotGameTurbo build support
26. Defined SELinux policy type for NotGameTurbo rules
27. Tuned properties to improve WiFi calling reliability
28. Removed unused repo dependencies
29. Switched to device-provided task_profiles.json
30. Cleaned up leftover legacy chmod lines in rootdir scripts
31. Added more ADPF profiles to powerhint configuration
32. Updated the WFD (Wireless Display) stack from marvel_g A171WEH.20
33. Moved network tuning to trigger on sys.boot_completed=1 for reliability
34. Added SELinux allow rules to fix multiple denials
35. Enabled sched_lib_mask_force for scheduler tuning
36. Imported the stock auto-brightness curve overlay
37. Added SELinux rules for ADPF config and the new powerhint setup
38. Added SELinux allow rules for MiuiCamera on SDK 37
39. Fixed remaining SELinux denials occurring during init
40. Redid several init-time tuning parameters
41. Reverted the earlier removal of GameBar
42. Conditionally switched product partition to EROFS on GMS builds
43. Migrated XiaomiParts UI to Material You Expressive (M3E)
44. Adapted device tree for the updated vendor/GMS structure
45. Set CPU hint percentage to 60
46. Force-disabled iorapd
47. Added a bypass-charging toggle and its QS tile
48. Allowed the lseek syscall for the atfwd daemon
49. Enabled additional framework overlays
50. Disabled GL backpressure for smoother rendering
51. Set minimum HWC/SurfaceFlinger duration to 8.4ms
52. Allowed the lseek syscall for qesdk-secmanager
53. Fixed ownership on the bypass-charging sysfs node
54. Restored LineageOS health HAL integration
55. Allowed the health HAL to access vendor battery-supply sysfs
56. Refactored powerhint node schema and removed an unused hint
57. Added CAMERA-specific powerhint hints
58. Overhauled the GAME powerhint profile and added ADPF profiles
59. Force-disabled REDIR_PARTY_NUM_SUPPORT
60. Updated included Soong namespaces
61. Switched kernel build toolchain to Clang r563880c
62. Synced with LineageOS trees

## Kernel
1. Improved CPU load balancing and PELT calculation accuracy
2. Reworked the cpuidle TEO governor — added a WFI timeout guard on arm64, dropped unnecessary sleep-length calls, reverted unstable upstream util-awareness patches
3. Isolated the prime core for heavy rendering threads
4. Speed up PELT utilization ramp-up
5. Enabled FullLTO build
6. Added and refined a generic wakelock blocker driver (Boeffla-based) with SM8635-specific blocklist entries and qcom_rx_wakelock blocking
7. ADDED SCENE BASED BYPASS CHARGING SUPPORT 
8. Hardened bypass charging support for the Qualcomm battery charger and switched the bypass scene to TGAME
9. Reduced devfreq polling interval to 50ms
10. Optimized the generic CPU idle loop, removing a needless memory barrier
11. Updated LZ4 to v1.9.4 and set zram's default compression algorithm to LZ4
12. Tuned the TCP/IP stack — fixed a build error, adjusted delayed ACKs, increased retransmission timeout, slowed congestion window growth
13. Reduced dynamic memory allocations in kernfs, DRM bridge, prctl_set_vma, and SELinux context buffers
14. Switched vmstat and DRM workqueues to power-efficient mode with a toggle
15. Started killing wakelocks after 2 minutes of idle
16. Ported a fingerprintd thaw hack from OnePlus 3
17. Sped up bpf map key/value handling and mbcache entry creation
18. Blocked various userspace bloatware services from running
19. Fixed and optimized PID maps output for arm64
20. Optimized console framebuffer for up to ~70% performance increase
21. Made RCU grace period workers unbound again and enabled panic-on-stall by default
22. Increased zram device count to 4
23. Improved cpuidle entry checks and fixed CPU_PM idle macro behavior
24. Suppressed excessive DTC compiler, CNTVCT, and suspend logging spam
25. Improved integer sqrt performance by ~3x
26. Increased the EXT4 default commit age
27. Synced with LineageOS trees

## Vendor
1. Updated firmware/vendor blobs to OS3.0.303.0.WNPMIXM
2. Updated the WFD (Wireless Display) stack from marvel_g A171WEH.20
3. Removed the unused sample qseecom client binary
4. Added libion dependency required by the ANC HAL
5. Added lseek sycall for qsedk and atwfd daemon
6. Force-disabled REDIR_PARTY_NUM_SUPPORT
7. Synced with LineageOS trees


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
