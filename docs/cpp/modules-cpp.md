---
title: C++ 中的模块概述
ms.date: 12/13/2019
helpviewer_keywords:
- modules [C++]
- modules [C++], overview
description: C + + 20 中的模块为标头文件提供了一种新式替代方法。
ms.openlocfilehash: 28e1824250ad4fb404c528aa9511745abb001f31
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301374"
---
# <a name="overview-of-modules-in-c"></a>C++ 中的模块概述

C + + 20 引入了*模块*，是用于组件化C++库和程序的新式解决方案。 模块是一组源代码文件，它们独立于导入它们的[翻译单元](https://wikipedia.org/wiki/Translation_unit_(programming))进行编译。 模块消除或大大减少了使用头文件时的许多问题，还可能会缩短编译时间。 在模块中声明的宏、预处理器指令和非导出名称不可见，因此不会影响导入模块的翻译单元的编译。 您可以按任何顺序导入模块，而无需考虑宏重新定义。 导入翻译单元中的声明不参与导入模块中的重载决策或名称查找。 模块编译一次后，结果将存储在一个二进制文件中，该文件描述所有导出的类型、函数和模板。 该文件的处理速度比标头文件快得多，并且可以由编译器在项目中导入模块的每个位置重复使用。

模块可与头文件并行使用。 C++源文件可以导入模块，还可以 #include 头文件中导入。 在某些情况下，可将标头文件作为模块导入，而不是由预处理器 #included。 建议新项目尽可能多地使用模块，而不是标头文件。 对于在活动开发下的较大现有项目，建议您尝试将旧式标头转换为模块，以查看编译时间是否获得有意义的缩减。

## <a name="enable-modules-in-the-microsoft-c-compiler"></a>在 Microsoft C++编译器中启用模块

Visual Studio 2019 版本16.2 中的模块未在 Microsoft C++编译器中完全实现。 你可以使用模块功能创建单分区模块，并导入 Microsoft 提供的标准库模块。 若要启用对模块的支持，请使用[/experimental： module](../build/reference/experimental-module.md)和[/std： c + + 最新版本](../build/reference/std-specify-language-standard-version.md)进行编译。 在 Visual Studio 项目中，右键单击**解决方案资源管理器**的项目节点，然后选择 "**属性**"。 将 "**配置**" 下拉箭头设置为 "**所有配置**"，然后选择 "**配置属性**" > **C/C++**  > **语言** > **启用C++模块（实验）** 。

模块和使用它的代码必须使用相同的编译器选项编译。

## <a name="consume-the-c-standard-library-as-modules"></a>将C++标准库用作模块

虽然 c + + 20 标准未指定，但 Microsoft 允许将C++标准库的实现作为模块导入。 通过将C++标准库作为模块导入（而不是通过头文件 #including），可以根据项目的大小，提高编译时间。 库被组件化到以下模块：

- std regex 提供标头的内容 \<regex >
- std filesystem 提供标头 \<filesystem 的内容 >
- std 提供标头 \<内存的内容 >
- std 提供标头的内容 \<原子 >、\<condition_variable >、\<未来 >、\<互斥 >、\<shared_mutex > 和 \<线程 >
- std 核心提供了标准库中的C++所有其他内容

若要使用这些模块，只需将导入声明添加到源代码文件的顶部。 例如：

```cpp
import std.core;
import std.regex;
```

若要使用 Microsoft 标准库模块，请使用[/ehsc](../build/reference/eh-exception-handling-model.md)和[/md](../build/reference/md-mt-ld-use-run-time-library.md)选项编译程序。

## <a name="basic-example"></a>基本示例

下面的示例在名为**ixx**的源文件中显示一个简单的模块定义。 Visual Studio 中的模块接口文件需要**ixx**扩展名。 在此示例中，接口文件包含函数定义和声明。 但是，还可以将定义放置在一个或多个单独的文件中（如后面的示例中所示）。 **导出模块 Foo**语句指示此文件是名为 `Foo`的模块的主要接口。 `f()` 上的**export**修饰符表示当其他程序或模块导入 `Foo` 时，此函数将可见。 请注意，该模块引用命名空间 `Bar`。

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

文件**myprogram.exe**使用**导入**声明访问 `Foo`导出的名称。 请注意，此处 `Bar` 名称是可见的，但并不是其所有成员。 另请注意，宏 `ANSWER` 不可见。

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

导入声明只能出现在全局范围。

## <a name="implementing-modules"></a>实现模块

您可以使用单个接口文件（. ixx）创建一个模块，该文件导出名称并包含所有函数和类型的实现。 你还可以将实现放在一个或多个单独的实现文件中，这与使用 .h 和 .cpp 文件的方式类似。 **Export**关键字仅用于接口文件中。 实现文件可以**导入**其他模块，但不能**导出**任何名称。 实现文件的名称可以有任何扩展名。 返回的接口文件和实现文件集被视为一种特殊类型的翻译单元，称为 "*模块单位*"。 在任何实现文件中声明的名称将自动显示在同一模块单元中的所有其他文件中。

对于较大的模块，可将模块拆分为多个称为 "*分区*" 的模块单元。 每个分区都包含一个或多个实现文件支持的接口文件。 （从 Visual Studio 2019 版本16.2 起，分区尚未完全实现。）

## <a name="modules-namespaces-and-argument-dependent-lookup"></a>模块、命名空间和与参数相关的查找

模块中命名空间的规则与任何其他代码中的规则相同。 如果导出命名空间中的声明，则还会隐式导出封闭命名空间（不包括非导出成员）。 如果显式导出命名空间，则会导出该命名空间定义中的所有声明。

在导入翻译单元中执行重载解析的参数相关查找时，编译器会将在同一转换单元（包括模块接口）中声明的函数视为函数参数的类型。已定义。

### <a name="module-partitions"></a>模块分区

> [!NOTE]
> 提供此部分是为了提供完整性。 Microsoft C++编译器尚未实现分区。

模块可以组件化到多个分区中，每个*分区*包含一个接口文件和零个或多个实现文件。 模块分区类似于模块，不同之处在于，它与整个模块中的所有声明共享所有权。 由分区接口文件导出的所有名称将由主接口文件导入并重新导出。 分区的名称必须以模块名称开头，后面跟一个冒号。 所有分区中的声明在整个模块中都可见。 避免出现一项定义规则（ODR）错误不需要任何特殊的预防措施。 可以在一个分区中声明一个名称（函数、类等），并在另一个分区中定义它。 分区实现文件的开头如下所示：

```cpp
module Foo:part1
```

分区接口文件的开头如下所示：

```cpp
export module Foo:part1
```

若要访问其他分区中的声明，分区必须导入它，但它只能使用分区名称，而不能使用模块名称：

```cpp
module Foo:part2;
import :part1;
```

主接口单元必须导入并重新导出模块的所有接口分区文件，如下所示：

```cpp
export import :part1
export import :part2
...
```

主接口单元可以导入分区实现文件，但不能将其导出，因为不允许这些文件导出任何名称。 这使模块能够使实现详细信息保留在模块内部。

## <a name="modules-and-header-files"></a>模块和标头文件

可以通过将 `#include` 指令置于模块声明之前，将标头文件包含在模块源文件中。 这些文件被视为位于*全局模块片段*中。 模块只能在它显式包含的标头中看到*全局模块片段*中的名称。 全局模块片段只包含实际使用的符号。

```cpp
// MyModuleA.cpp

#include "customlib.h"
#include "anotherlib.h"

import std.core;
import MyModuleB;

//... rest of file
```

您可以使用传统的标头文件来控制要导入的模块：

```cpp
// MyProgram.h
import std.core;
#ifdef DEBUG_LOGGING
import std.filesystem;
#endif
```

### <a name="imported-header-files"></a>导入的标头文件

> [!NOTE]
> 本节仅提供信息。 旧版导入尚未在 Microsoft C++编译器中实现。

一些标头完全是独立的，它们允许使用**import**关键字进入。 导入的标头与导入的模块之间的主要区别是：头中的任何预处理器定义在 import 语句之后立即显示在导入程序中。 （该标头包含的任何文件中的预处理器定义都*不*可见。）

```cpp
import <vector>
import "myheader.h"
```

## <a name="see-also"></a>另请参阅

[模块，导入，导出](import-export-module.md)
