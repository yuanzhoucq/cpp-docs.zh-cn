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
ms.openlocfilehash: ae28bce8e06840cafa5c92521f6e9a62aa5bfde6
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301452"
---
# <a name="module-import-export"></a>模块，导入，导出

**模块**、**导入**和**导出**声明在 c + + 20 中提供，并且需要[/experimental： module](../build/reference/experimental-module.md)编译器开关和[/std： C + + 最新版本](../build/reference/std-specify-language-standard-version.md)。 有关详细信息，请参阅[ C++中模块概述](modules-cpp.md)。

## <a name="module"></a>name

将**模块**声明置于模块实现文件的开头，以指定该文件的内容属于命名模块。

```cpp
module ModuleA;
```

## <a name="export"></a>export

为模块的主接口文件（必须具有扩展名**ixx**）使用**导出模块**声明：

```cpp
export module ModuleA;
```

在接口文件中，对要作为公共接口的一部分的名称使用**export**修饰符：

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

void main() {
  Bar::f(); // OK
  Bar::d(); // OK
  Bar::internal_f(); // Ill-formed: error C2065: 'internal_f': undeclared identifier
}
```

**Export**关键字不能出现在模块实现文件中。 将**导出**应用于命名空间名称时，将导出命名空间中的所有名称。

## <a name="import"></a>导入

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

在 Microsoft C++中，当用作宏的参数时，令牌**导入**和**模块**始终是标识符，而不是关键字。

### <a name="example"></a>示例

```cpp
#define foo(…) __VA_ARGS__
foo(
import // Always an identifier, never a keyword
)
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[模块概述C++](modules-cpp.md)
