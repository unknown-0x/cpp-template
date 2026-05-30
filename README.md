<h1 align="center">cpp-template</h1>

<p align="center">
  <strong>A minimal C++ project starter template using CMake.</strong>
</p>

---

## Template Structure

This project follows a simple C++ layout:

- `src/` — contains the main source code of the project
- `tests/` — contains all test cases for testing the codebase

This separation keeps production and test code organized and maintainable.

---

## Project Name

In `CMakeLists.txt`, you can change "project" to your own project name:

```cmake
project(
    "project"
    VERSION 1.0.0
    LANGUAGES CXX C
)
```

---

## Building & Testing

### Prerequisites

- **CMake** >= 3.15
- **Ninja** (required for `ninja` and `msvc` presets)
- A supported toolchain (GCC/Clang for Linux/macOS, MSVC/clang-cl for Windows)

| Platform / Toolchain      | Build Type             | Configure Preset                             | Build Preset                                 | Test Preset                                  |
| :------------------------ | :--------------------- | :------------------------------------------- | :------------------------------------------- | :------------------------------------------- |
| **Linux / macOS** (Ninja) | `Debug` <br> `Release` | `ninja-debug` <br> `ninja-release`           | `ninja-debug` <br> `ninja-release`           | `ninja-debug` <br> `ninja-release`           |
| **Windows** (MSVC)        | `Debug` <br> `Release` | `msvc-debug` <br> `msvc-release`             | `msvc-debug` <br> `msvc-release`             | `msvc-debug` <br> `msvc-release`             |
| **Windows** (clang-cl)    | `Debug` <br> `Release` | `msvc-clang-debug` <br> `msvc-clang-release` | `msvc-clang-debug` <br> `msvc-clang-release` | `msvc-clang-debug` <br> `msvc-clang-release` |

**Usage Example:**

```bash
# Configure Preset
cmake --preset ninja-release

# Build Preset
cmake --build --preset ninja-release

# Test Preset (if `BUILD_TESTING` is enabled)
ctest --preset ninja-release
```

---

## CMake Options

This template provides several configurable CMake options:

### `CMAKE_CXX_STANDARD`
- **Default:** `17`
- Defines the C++ standard used to build the project.
- Example: `17`, `20`


### `WARNINGS_AS_ERRORS`
- **Default:** `OFF`
- When enabled, compiler warnings will be treated as errors.


### `BUILD_SHARED_LIBS`
- **Default:** `OFF`
- Controls the type of library build:
  - `OFF` : static library
  - `ON` : shared library (`.so`, `.dll`, `.dylib`)


### `BUILD_TESTING`
- **Default:** `ON`
- Enables or disables building tests.
- When `OFF`, test targets will not be generated.


### `ENABLE_CLANG_TIDY`
- **Default:** `OFF`
- Enables static analysis using `clang-tidy`.
- Useful for code quality checks and catching potential issues early.
> **Note:** If `ENABLE_CLANG_TIDY` is set to `ON` but `clang-tidy` is not installed or not found in the system PATH, the check will be automatically skipped.
