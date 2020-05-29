---
title: 模块，导入，导出
ms.date: 12/12/2019
f1_keywords:
- module_cpp
- import_cpp
- export_cpp
helpviewer_keywords:
- modules [C++]
- modules [C++], import
- modules [C++], export
description: 使用导入和导出声明访问并发布指定模块中定义的类型和函数。
ms.openlocfilehash: a765e9a406660d3c945ef3d70754178b0648458c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374114"
---
# <a name="module-import-export"></a>模块，导入，导出

**模块**、**导入**和**导出**声明在 C++20 中可用，并且需要[/实验：模块](../build/reference/experimental-module.md)编译器开关以及[/std：c_最新](../build/reference/std-specify-language-standard-version.md)。 有关详细信息，请参阅[C++ 中的模块概述](modules-cpp.md)。

## <a name="module"></a>module

将**模块**声明放在模块实现文件的开头，以指定文件内容属于命名模块。

```cpp
module ModuleA;
```

## <a name="export"></a>导出

对模块的主接口文件使用**导出模块**声明，该文件必须具有扩展**名 .ixx**：

```cpp
export module ModuleA;
```

在接口文件中，对打算成为公共接口一部分的名称使用**导出**修改器：

```cpp
// ModuleA.ixx

export module ModuleA;

namespace Bar
{
   export int f();
   export double d();
   double internal_f(); // not exported
}
```

导入模块的代码看不到非导出的名称：

```cpp
//MyProgram.cpp

import module ModuleA;

int main() {
  Bar::f(); // OK
  Bar::d(); // OK
  Bar::internal_f(); // Ill-formed: error C2065: 'internal_f': undeclared identifier
}
```

**导出**关键字可能不会显示在模块实现文件中。 当**导出**应用于命名空间名称时，将导出命名空间中的所有名称。

## <a name="import"></a>进口

使用**导入**声明使模块的名称在程序中可见。 导入声明必须出现在模块声明之后和任何#include指令之后，但在文件中的任何声明之前。

```cpp
module ModuleA;

#include "custom-lib.h"
import std.core;
import std.regex;
import ModuleB;

// begin declarations here:
template <class T>
class Baz
{...};
```

## <a name="remarks"></a>备注

**导入**和**模块**仅在逻辑行的开头出现时被视为关键字：

```cpp

// OK:
module ;
module module-name
import :
import <
import "
import module-name
export module ;
export module module-name
export import :
export import <
export import "
export import module-name

// Error:
int i; module ;
```

**微软特定**

在 Microsoft C++中，**导入**的令牌和**模块**在用作宏的参数时始终是标识符，从不为关键字。

### <a name="example"></a>示例

```cpp
#define foo(…) __VA_ARGS__
foo(
import // Always an identifier, never a keyword
)
```

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[C++ 中的模块概述](modules-cpp.md)
