# testing_something_for_dart

```dart
import 'dart:io';

/// Class to represent an asset file.
class FileAsset {
  final String filePath;

  FileAsset(this.filePath);

  String get fileExtension => filePath.split('.').last;
}

/// Extension methods for FileAsset class.
extension FileAssetExtension on FileAsset {
  Extension get extension => _getExtension(fileExtension);
  Type get type => _getType(fileExtension);
}

/// Determine the extension type.
Extension _getExtension(String ext) {
  switch (ext) {
    // Image extensions
    case 'png':
      return Extension.png;
    case 'jpeg':
      return Extension.jpeg;
    case 'webp':
      return Extension.webp;
    // Font extensions
    case 'otf':
      return Extension.otf;
    case 'ttf':
      return Extension.ttf;
    // Shader extensions
    case 'frag':
      return Extension.shader;
    case 'vert':
      return Extension.shader;
    case 'geom':
      return Extension.shader;
    case 'comp':
      return Extension.shader;
    case 'glsl':
      return Extension.glsl;
    case 'spv': // SPIR-V file extension
      return Extension.spv;
    // Audio extensions
    case 'mp3':
      return Extension.mp3;
    case 'wav':
      return Extension.wav;
    case 'aac':
      return Extension.aac;
    case 'ogg':
      return Extension.ogg;
    case 'flac':
      return Extension.flac;
    case 'm4a':
      return Extension.m4a;
    // Video extensions
    case 'mp4':
      return Extension.mp4;
    case 'mov':
      return Extension.mov;
    case 'avi':
      return Extension.avi;
    case 'mkv':
      return Extension.mkv;
    case 'wmv':
      return Extension.wmv;
    // Lottie extensions
    case 'lottie':
      return Extension.lottie;
    // Rive extensions
    case 'riv':
      return Extension.rive;
    case 'flr':
      return Extension.rive;
  }
  return Extension.unknown;
}

/// Determine the asset type.
Type _getType(String ext) {
  switch (ext) {
    // Image types
    case 'png':
    case 'jpeg':
    case 'webp':
      return Type.image;
    // Font types
    case 'otf':
    case 'ttf':
      return Type.font;
    // Shader types
    case 'frag':
    case 'vert':
    case 'geom':
    case 'comp':
    case 'glsl':
    case 'spv':
      return Type.shader;
    // Audio types
    case 'mp3':
    case 'wav':
    case 'aac':
    case 'ogg':
    case 'flac':
    case 'm4a':
      return Type.audio;
    // Video types
    case 'mp4':
    case 'mov':
    case 'avi':
    case 'mkv':
    case 'wmv':
      return Type.video;
    // Lottie types
    case 'lottie':
      return Type.lottie;
    // Rive types
    case 'riv':
    case 'flr':
      return Type.rive;
  }
  return Type.unknown;
}

/// Asset file extension enum.
enum Extension {
  // Image extensions
  png,
  jpeg,
  webp,
  // Font extensions
  otf,
  ttf,
  // Shader extensions
  frag,
  vert,
  geom,
  comp,
  glsl,
  spv,
  // Audio extensions
  mp3,
  wav,
  aac,
  ogg,
  flac,
  m4a,
  // Video extensions
  mp4,
  mov,
  avi,
  mkv,
  wmv,
  // Lottie extensions
  lottie,
  // Rive extensions
  riv,
  flr,
  // Unknown extension
  unknown,
}

/// Asset type enum.
enum Type {
  image,
  font,
  shader,
  audio,
  video,
  lottie,
  rive,
  unknown,
}

```


# Testing

```dart
import 'platform_native.dart' if (dart.library.html) 'platform_web.dart';

abstract class Platform {
  bool get isTesting;
  static final Platform instance = makePlatform();
}
```

```dart

import 'dart:io' as io show Platform;

import 'platform.dart';

Platform makePlatform() => PlatformNative();

class PlatformNative extends Platform {
  @override
  bool get isTesting => io.Platform.environment.containsKey('FLUTTER_TEST');
}
```


```dart

import 'platform.dart';

Platform makePlatform() => PlatformWeb();

class PlatformWeb extends Platform {
  @override
  bool get isTesting => false;
}
```
