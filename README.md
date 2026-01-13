ICS/Sensus Live Wallpaper (Modern Android)
📌 Overview
This project replicates the classic Sensus/ICS live wallpaper for modern Android (AndroidX, Android 12+). It uses OpenGL ES 2.0 for smooth animations and supports customization via a settings screen.

✅ Features

Animated Particles with glow effect.
Dynamic Style Switching:

Standard
Phase Beam
Sense
Smooth


Parallax Effect when swiping home screens.
Customizable Settings:

Speed
Parallax intensity
FPS limit
Style selection
Tint color overlay


Fade-in Effect when wallpaper becomes visible.
Performance Optimizations:

FPS capping
VBO support for particles
Reduced GC pressure




🏗 Architecture
WallpaperService (GLSensusWallpaperService)
    └── Engine
         └── GLSurfaceView
              └── SensusRenderer (OpenGL ES 2.0)

Components

GLSensusWallpaperService
Handles wallpaper lifecycle and visibility changes.
SettingsActivity
Provides UI for customization (speed, parallax, style, tint).
SensusRenderer
Draws particles and background using OpenGL ES 2.0.
prefs_live_wallpaper.xml
Defines user preferences.


🎨 Assets
Place these in res/drawable/:

wallpaper2.png → Standard
classic.png → Phase Beam
sensewp.png → Sense
wallpaper.png → Smooth


⚙️ Setup Instructions

Clone the repository.
Open in Android Studio.
Ensure minSdkVersion ≥ 21 and targetSdkVersion ≥ 33.
Add required permissions in AndroidManifest.xml:
XML<uses-permission android:name="android.permission.SET_WALLPAPER" />Show more lines

Build and run on a device/emulator.
Apply wallpaper via Wallpaper & Style → Live Wallpapers → ICS/Sensus Wallpaper.


🔧 Customization

Preferences are stored in SharedPreferences and handled by SensusRenderer.
Keys:

prefkeyBGStyle → Style selection
prefkeyTintColor → Tint color (#AARRGGBB)
prefkeySpeed → Particle speed
prefkeyParallax → Parallax intensity
prefkeyFps → FPS limit




✅ Testing Checklist

Apply wallpaper → particles animate smoothly.
Swipe home screens → parallax responds.
Change style in settings → background updates instantly.
Adjust tint → color overlay applies.
Lock/unlock → fade-in effect works.
FPS preference → frame pacing adjusts.


🛠 Advanced Features

Auto Style Changer (optional): Rotate styles periodically.
Gradient Backgrounds: Modify fragment shader for dynamic gradients.
Performance:

Use VBOs for particle batching.
Minimize allocations in render loop.




📜 Why 32-bit Color (ARGB_8888)?

Full color fidelity (8 bits per channel).
Alpha transparency for glow and fade effects.
Alternatives like RGB_565 reduce quality and remove alpha.


📂 Files to Check

GLSensusWallpaperService.java
SensusRenderer.java
SettingsActivity.java
prefs_live_wallpaper.xml
arrays.xml (style entries)


✅ Next Steps for Maintainer

Verify assets exist in res/drawable/.
Confirm preference keys match renderer logic.
Profile performance on real devices.
Consider adding Material You dynamic color support.
