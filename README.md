# OpenATL

A clean-room, minimal reimplementation of Microsoft's Active Template Library (ATL) for non-Windows platforms.

## Purpose

OpenATL enables compiling and testing [WTL](https://wtl.sourceforge.io) (Windows Template Library) applications on non-Windows platforms using cross-compilers. Since WTL depends on ATL headers that are only available in Microsoft's toolchain, OpenATL provides the subset of ATL required by WTL, allowing development and CI builds on macOS and Linux.

## Features

- Header-only library, no build step required
- C++17 standard
- Supports WTL 10.0
- Clean-room implementation (no Microsoft or ReactOS code)
- Provides: `atlbase.h`, `atlwin.h`, `atlcom.h`, `atlstr.h`, `atltypes.h`, and supporting headers

## Implemented ATL Components

| Header | Contents |
|--------|----------|
| `atldef.h` | Base macros (`ATLASSERT`, `ATLVERIFY`, `AtlThrow`, `ATL_NO_VTABLE`, etc.) |
| `atlcore.h` | `CComCriticalSection`, `CAtlBaseModule`, string resource helpers |
| `atlalloc.h` | `CCRTAllocator`, `CHeapPtr`, `CTempBuffer` |
| `atlsimpcoll.h` | `CSimpleArray`, `CSimpleMap` |
| `atlcomcli.h` | `CComPtr`, `CComQIPtr`, `CComBSTR`, `CComVariant` |
| `atltrace.h` | `ATLTRACE`, `ATLTRACE2`, trace categories |
| `atlbase.h` | `CComModule`, `CAtlModule`, `CRegKey`, `CHandle`, threading models, `ATL::Checked` namespace |
| `atlwin.h` | `CWindow`, `CWindowImpl`, `CDialogImpl`, `CContainedWindow`, message map macros, thunks (x86, x86_64, AArch64) |
| `atlcom.h` | `CComObjectRootEx`, `CComObject`, COM map macros |
| `atlstr.h` | `CString` (based on `CSimpleStringT`) |
| `atltypes.h` | `CPoint`, `CSize`, `CRect` |

## Verified Compiler

Tested and verified with [llvm-mingw](https://github.com/mstorsjo/llvm-mingw) (Clang/MinGW cross-compiler toolchain).

## Usage

Add the `include` directory to your include path:

```cmake
target_include_directories(your_target PRIVATE path/to/openatl/include)
```

Then include ATL headers as usual:

```cpp
#include <atlbase.h>
#include <atlwin.h>
```

## Demo

See [wtltest](https://github.com/kkHAIKE/wtltest) for a comprehensive WTL 10.0 test application built with OpenATL.

## Author

Created by Claude Opus (Anthropic).

## License

MIT License. See [LICENSE](LICENSE) for details.
