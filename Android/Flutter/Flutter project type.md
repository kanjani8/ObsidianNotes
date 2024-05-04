1. **Application**:
    
    - This is ==the most common type== of project used to create full-fledged(본격적인) Flutter applications. It sets up a structure that includes everything needed to build and run a mobile, web, or desktop application.
2. **Plugin**:
    
    - A plugin project is used when you want to create reusable code that can interact with platform-specific APIs on iOS, Android, web, or desktop. Plugins can be used to access device features like the camera, GPS, or native file system that are not available in the Flutter framework by default.
3. **Package**:
    
    - Packages are a way to create reusable Dart code that can be shared across multiple Flutter or Dart applications. A package can include Flutter-specific libraries (widgets, utilities), pure Dart libraries, or a combination of both. It doesn't include any native code integration.
4. **Module**:
    - A module is a subset of a Flutter application that can be integrated into an existing native iOS or Android application. ==This is useful if you want to incrementally introduce Flutter into existing mobile applications== by embedding the Flutter runtime and your Dart code as a library or module within the native framework.
5. **Skeleton**:
    - This project type sets up a bare-bones Flutter project with ==minimal pre-built UI==. It's ideal if you want to start from scratch or ==need a minimal setup for a proof of concept== or a simple test.
6. **FFI Plugin**:
    - FFI (Foreign Function Interface) plugins allow you to call C-based APIs from Dart. This is particularly useful when you need to execute native code for operations that require high performance or need to interface directly with an existing C library. This project type sets up a template for integrating with C code using Dart FFI.

#Flutter  #Android  #Mobile 