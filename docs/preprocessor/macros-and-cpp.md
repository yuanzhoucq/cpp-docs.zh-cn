---
title: 宏和 C++
ms.date: 08/29/2019
helpviewer_keywords:
- macros, C++
- macros
ms.assetid: 83a344c1-73c9-4ace-8b93-cccfb62c6133
ms.openlocfilehash: 8a86fb81544af91d4e844fb08b7948a589976e04
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220801"
---
# <a name="macros-and-c"></a>宏和 C++

C++提供了一些新的功能, 其中一些取代由 ANSI C 预处理器提供。 这些新功能可增强语言的类型安全性和可预见性：

- 在C++中, 可以在常量表达式中使用声明为**const**的对象。 它允许程序声明具有类型和值信息的常量。 它们可以声明可通过调试器符号查看的枚举。 使用预处理器`#define`指令定义常量时, 它不是精确的, 也不是类型安全的。 不会为**const**对象分配存储, 除非该程序包含采用其地址的表达式。

- C++ 内联函数功能取代了函数类型宏。 使用内联函数取代宏的好处如下：

  - 类型安全。 内联函数需要接受与常规函数相同的类型检查。 宏不是类型安全的。

  - 纠正具有副作用的参数的处理。 内联函数计算在输入函数体前作为参数提供的表达式。 因此, 具有副作用的表达式并不安全。

有关内联函数的详细信息, 请参阅[inline、__inline \_、_forceinline](../cpp/inline-functions-cpp.md)。

出于向后兼容性的原因，将为 Microsoft C++ 保留存在于 ANSI C 以及更早的 C++ 规范中的所有预处理器工具。

## <a name="see-also"></a>请参阅

[预定义的宏](../preprocessor/predefined-macros.md)\
[宏 (C/C++)](../preprocessor/macros-c-cpp.md)
