# P.T. iOS Port

This branch is the native iOS port of the C++ P.T. PC implementation. It does not contain P.T. game data; users must provide their own legally obtained extracted game files.

## Current status

- iOS ARM64 CMake/toolchain target: started
- SDL3 iOS integration: pending build validation
- Vulkan/MoltenVK: pending integration and device build
- iOS filesystem/data import: pending
- touch controls: pending
- voice/microphone: pending
- unsigned IPA packaging: pending

## First device build

From a macOS machine with Xcode, CMake, and the Vulkan SDK/MoltenVK available:

    cmake -S . -B build-ios -G Xcode -DCMAKE_TOOLCHAIN_FILE=cmake/iOS.cmake
    cmake --build build-ios --config Release -- -sdk iphoneos CODE_SIGNING_ALLOWED=NO CODE_SIGNING_REQUIRED=NO

The resulting pt.app is the first milestone. This is intentionally an unsigned development build; signing/install packaging comes after the renderer and data path are working.

## Architecture

The port keeps the existing C++ engine and SDL3 input/render loop. iOS-specific behavior should live behind the existing src/engine/platform abstractions or small iOS-only files rather than changing Windows/Linux behavior.
