---
title: C++ 中的模块概述
ms.date: 12/13/2019
helpviewer_keywords:
- modules [C++]
- modules [C++], overview
description: C++20 中的模块提供了标头文件的现代替代方法。
ms.openlocfilehash: cd45be1dee888c8caeb65b7ff002ac8fee1ecbe1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370763"
---
# <a name="overview-of-modules-in-c"></a>C++ 中的模块概述

C++20 引入了*模块*，这是C++库和程序组件化的现代解决方案。 模块是一组源代码文件，它们独立于导入它们的[翻译单元](https://wikipedia.org/wiki/Translation_unit_(programming))进行编译。 模块消除或大大减少了与使用标头文件相关的许多问题，还可能减少编译时间。 模块中声明的宏、预处理器指令和非导出名称不可见，因此对导入模块的翻译单元的编译没有影响。 您可以按任意顺序导入模块，而无需考虑宏重新定义。 导入翻译单元中的声明不参与导入模块中的重载解析或名称查找。 编译一次模块后，结果将存储在描述所有导出类型、函数和模板的二进制文件中。 该文件的处理速度可以比头文件快得多，并且编译器可以在项目中导入模块的每个位置重用该文件。

模块可以并排使用，与头文件一起使用。 C++源文件可以导入模块，也可以#include头文件。 在某些情况下，头文件可以作为模块导入，而不是由预处理器以文本#included。 我们建议新项目尽可能使用模块而不是头文件。 对于正在积极开发的大型现有项目，我们建议您尝试将旧标头转换为模块，以查看是否有效减少了编译时间。

## <a name="enable-modules-in-the-microsoft-c-compiler"></a>启用 Microsoft C++编译器中的模块

自 Visual Studio 2019 版本 16.2 起，模块未在 Microsoft C++编译器中完全实现。 您可以使用模块功能创建单分区模块并导入 Microsoft 提供的标准库模块。 要启用对模块的支持，使用[/实验：模块](../build/reference/experimental-module.md)和[/std：c_最新](../build/reference/std-specify-language-standard-version.md)编译。 在可视化工作室项目中，右键单击**解决方案资源管理器**中的项目节点并选择**属性**。 将 **"配置**"下拉列表**设置为"所有配置**"，然后选择**配置属性** > **C/C++** > **语言** > **启用C++模块（实验）。**

模块和使用它的代码必须使用相同的编译器选项进行编译。

## <a name="consume-the-c-standard-library-as-modules"></a>将C++标准库用作模块

尽管 C++20 标准未指定，但 Microsoft 允许将其C++标准库的实现作为模块导入。 通过将C++标准库导入为模块，而不是通过头文件#including它，您可以根据项目的大小加快编译时间。 该库已组件化为以下模块：

- std.regex 提供标头\<正则表达式>的内容
- std.filesystem 提供头\<文件系统的内容>
- std.memory 提供标头\<内存>
- std.streading 提供标头\<原子>、condition_variable>、\<\<未来>、\<互斥>、shared_mutex>\<和\<线程>
- std.core 提供C++标准库中的其他所有内容

要使用这些模块，只需将导入声明添加到源代码文件的顶部即可。 例如：

```cpp
import std.core;
import std.regex;
```

要使用 Microsoft 标准库模块，请使用[/EHsc](../build/reference/eh-exception-handling-model.md)和[/MD](../build/reference/md-mt-ld-use-run-time-library.md)选项编译程序。

## <a name="basic-example"></a>基本示例

下面的示例显示了名为**Foo.ixx**的源文件中的简单模块定义。 Visual Studio 中的模块接口文件需要 **.ixx**扩展名。 在此示例中，接口文件包含函数定义以及声明。 但是，定义也可以放置在一个或多个单独的文件中（如后面的示例所示）。 **导出模块 Foo**语句指示此文件是称为`Foo`模块的主接口。 `f()`上的**导出**修改器指示当由其他程序或模块导入时`Foo`，此函数将可见。 请注意，模块引用命名空间`Bar`。

```cpp
export module Foo;

#define ANSWER 42

namespace Bar
{
   int f_internal() {
        return ANSWER;
      }

   export int f() {
      return f_internal();
   }
}
```

文件**MyProgram.cpp**使用**导入**声明访问由`Foo`导出的名称。 请注意，该名称`Bar`在此处可见，但不是其所有成员。 另请注意，宏`ANSWER`不可见。

```cpp

import Foo;
import std.core;

using namespace std;

int main()
{
   cout << "The result of f() is " << Bar::f() << endl; // 42
   // int i = Bar::f_internal(); // C2039
   // int j = ANSWER; //C2065
}

```

导入声明只能出现在全局作用域中。

## <a name="implementing-modules"></a>实现模块

您可以创建一个包含单个接口文件 （.ixx） 的模块，该文件导出名称，并包含所有函数和类型的实现。 您还可以将实现放在一个或多个单独的实现文件中，类似于 .h 和 .cpp 文件的使用方式。 **导出**关键字仅在接口文件中使用。 实现文件可以**导入**另一个模块，但不能**导出**任何名称。 可以使用任何扩展名命名实现文件。 接口文件和支持它的实现文件集被视为一种称为*模块单元*的特殊类型的翻译单元。 在任何实现文件中声明的名称在同一模块单元中的所有其他文件中自动可见。

对于较大的模块，您可以将模块拆分为多个模块单元，称为*分区*。 每个分区由一个或多个实现文件支持的接口文件组成。 （截至 Visual Studio 2019 版本 16.2，分区尚未完全实现。

## <a name="modules-namespaces-and-argument-dependent-lookup"></a>模块、命名空间和与参数相关的查找

模块中的命名空间规则与任何其他代码的规则相同。 如果导出命名空间中的声明，则封闭命名空间（不包括非导出成员）也将隐式导出。 如果显式导出命名空间，则导出该命名空间定义中的所有声明。

在导入转换单元中执行与参数相关的查找重载解析时，编译器将在同一转换单元（包括模块接口）中声明的函数视为定义函数参数类型的函数。

### <a name="module-partitions"></a>模块分区

> [!NOTE]
> 此部分是完整性的提供。 分区尚未在 Microsoft C++编译器中实现。

模块可以组件化为分区，每个*分区*由接口文件和零个或多个实现文件组成。 模块分区类似于模块，只不过它共享整个模块中所有声明的所有权。 分区接口文件导出的所有名称都由主接口文件导入和重新导出。 分区的名称必须以模块名称后跟冒号开头。 任何分区中的声明在整个模块中可见。 无需采取特殊预防措施即可避免单定义规则 （ODR） 错误。 您可以在一个分区中声明名称（函数、类等），并在另一个分区中定义它。 分区实现文件开始如下所示：

```cpp
module Foo:part1
```

分区接口文件开始如下所示：

```cpp
export module Foo:part1
```

要访问另一个分区中的声明，分区必须导入它，但它只能使用分区名称，而不能使用模块名称：

```cpp
module Foo:part2;
import :part1;
```

主接口单元必须导入和重新导出模块的所有接口分区文件，如下所示：

```cpp
export import :part1
export import :part2
...
```

主接口单元可以导入分区实现文件，但不能导出这些文件，因为不允许导出任何名称。 这使模块能够将实现详细信息保留到模块的内部。

## <a name="modules-and-header-files"></a>模块和标头文件

通过将指令放在模块声明之前，`#include`可以在模块源文件中包含标头文件。 这些文件被认为是在*全局模块片段*中。 模块只能看到它显式包含的标头中的*全局模块片段*中的名称。 全局模块片段仅包含实际使用的符号。

```cpp
// MyModuleA.cpp

#include "customlib.h"
#include "anotherlib.h"

import std.core;
import MyModuleB;

//... rest of file
```

您可以使用传统的标头文件来控制导入的模块：

```cpp
// MyProgram.h
import std.core;
#ifdef DEBUG_LOGGING
import std.filesystem;
#endif
```

### <a name="imported-header-files"></a>导入的标头文件

> [!NOTE]
> 本节仅供参考。 旧导入尚未在 Microsoft C++编译器中实现。

某些标头足够自包含，允许使用**import**关键字引入它们。 导入的标头和导入模块之间的主要区别是，标头中的任何预处理器定义在导入语句后立即在导入程序中可见。 （该标头包含的任何文件中的预处理器定义*不可见*。

```cpp
import <vector>
import "myheader.h"
```

## <a name="see-also"></a>另请参阅

[模块，导入，导出](import-export-module.md)
