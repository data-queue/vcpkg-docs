---
title: vcpkg_fixup_pkgconfig
description: Learn how to use vcpkg_fixup_pkgconfig.
ms.date: 01/10/2024
---
# vcpkg_fixup_pkgconfig

Fix common paths in *.pc files and make everything relative to `$(prefix)`.

Additionally, on static triplets, private entries are merged with their non-private counterparts, allowing pkg-config to be called without the ``--static`` flag.

Since a consumer cannot know if a dependent library has been built statically or not, vcpkg is designed to never have to call pkg-config with the ``--static`` flag.

## Usage

```cmake
vcpkg_fixup_pkgconfig(
    [RELEASE_FILES <PATHS>...]
    [DEBUG_FILES <PATHS>...]
    [SKIP_CHECK]
)
```

## Parameters

### RELEASE_FILES

Specifies a list of files to apply the fixes for release paths. Defaults to every *.pc file in the folder `${CURRENT_PACKAGES_DIR}` without `${CURRENT_PACKAGES_DIR}/debug/`

### DEBUG_FILES

Specifies a list of files to apply the fixes for debug paths. Defaults to every *.pc file in the folder `${CURRENT_PACKAGES_DIR}/debug/`

### SKIP_CHECK

Skips the library checks in `vcpkg_fixup_pkgconfig`. Only use if the script itself has unhandled cases.

### SYSTEM_PACKAGES (deprecated)

> [!WARNING]
> This argument has been deprecated and has no effect.

### SYSTEM_LIBRARIES (deprecated)

> [!WARNING]
> This argument has been deprecated and has no effect.

### IGNORE_FLAGS (deprecated)

> [!WARNING]
> This argument has been deprecated and has no effect.

## Notes

Still a work in progress. If there are more cases which can be handled here feel free to add them.

## Examples

- [brotli](https://github.com/Microsoft/vcpkg/blob/master/ports/brotli/portfile.cmake)

## Source

[`scripts/cmake/vcpkg_fixup_pkgconfig.cmake`](https://github.com/Microsoft/vcpkg/blob/master/scripts/cmake/vcpkg_fixup_pkgconfig.cmake)
