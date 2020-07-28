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
description: 使用导入和导出声明可以访问和发布在指定模块中定义的类型和函数。
ms.openlocfilehash: 5be1618d7e64f6887cf78bd863d428d6710eaf7e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87187187"
---
# <a name="module-import-export"></a>模块，导入，导出

**模块**、**导入**和 **`export`** 声明在 c + + 20 中可用，并且需要[/experimental： module](../build/reference/experimental-module.md)编译器开关和[/std： C + + 最新版本](../build/reference/std-specify-language-standard-version.md)。 有关详细信息，请参阅[c + + 中模块概述](modules-cpp.md)。

## <a name="module"></a>name

将**模块**声明置于模块实现文件的开头，以指定该文件的内容属于命名模块。

```cpp
module ModuleA;
```

## <a name="export"></a>导出

为模块的主接口文件（必须具有扩展名**ixx**）使用**导出模块**声明：

```cpp
export module ModuleA;
```

在接口文件中，对要 **`export`** 作为公共接口的一部分的名称使用修饰符：

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

导入模块的代码不会显示非导出名称：

```cpp
//MyProgram.cpp

import module ModuleA;

int main() {
  Bar::f(); // OK
  Bar::d(); // OK
  Bar::internal_f(); // Ill-formed: error C2065: 'internal_f': undeclared identifier
}
```

**`export`** 关键字不能出现在模块实现文件中。 当 **`export`** 应用于命名空间名称时，将导出命名空间中的所有名称。

## <a name="import"></a>进口

使用**导入**声明使模块的名称在您的程序中可见。 导入声明必须出现在模块声明之后以及任何 #include 指令之后、但在文件中的任何声明之前。

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

仅当**import**和**module**出现在逻辑行的开头时，它们才被视为关键字：

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

**Microsoft 专用**

在 Microsoft c + + 中，当将标记**导入**和**模块**用作宏的自变量时，它们始终为标识符和从不关键字。

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
