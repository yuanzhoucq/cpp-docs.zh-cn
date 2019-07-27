---
title: 模块, 导入, 导出
ms.date: 07/15/2019
f1_keywords:
- module_cpp
- import_cpp
- export_cpp
helpviewer_keywords:
- modules [C++]
- modules [C++], import
- modules [C++], export
description: 使用 import 语句可访问指定模块中定义的类型和函数。
ms.openlocfilehash: fbb9c45ec816c859edb4df38ad67dc7778247e87
ms.sourcegitcommit: 7b039b5f32f6c59be6c6bb1cffafd69c3bfadd35
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/26/2019
ms.locfileid: "68537783"
---
# <a name="module-import-export"></a>模块, 导入, 导出

在 `/std:c++latest`c++ 20 中提供了模块、**导入**和**导出**关键字, 并要求编译器开关与一起使用。`/experimental:modules` 有关详细信息, 请参阅[ C++中模块概述](modules-cpp.md)。

## <a name="module"></a>name

使用模块实现文件开头的**module**语句来指定文件内容属于命名模块。 

```cpp
module ModuleA;
```

## <a name="export"></a>export

对模块的主接口文件使用**export module**语句, 该文件必须具有扩展名 **. ixx**:

```cpp
export module ModuleA;
```

在接口文件中, 对要作为公共接口的一部分的名称使用**export**修饰符:

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

导入模块的代码不会显示非导出名称:

```cpp
//MyProgram.cpp

import module ModuleA;

void main() {
  Bar::f(); // OK
  Bar::d(); // OK
  Bar::internal_f(); // Ill-formed: error C2065: 'internal_f': undeclared identifier
}
```

**Export**关键字不能出现在模块实现文件中。 当**export**修饰符应用于命名空间名称时, 将导出命名空间中的所有名称。

## <a name="import"></a>import

使用**import**语句使模块的名称在您的程序中可见。 Import 语句必须出现在 module 语句之后、任何 #include 指令之后、但在文件中的任何声明之前。

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

## <a name="see-also"></a>请参阅
[模块概述C++](modules-cpp.md)
