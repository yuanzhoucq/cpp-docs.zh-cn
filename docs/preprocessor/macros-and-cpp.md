---
title: 宏和 C++
ms.date: 11/04/2016
helpviewer_keywords:
- macros, C++
- macros
ms.assetid: 83a344c1-73c9-4ace-8b93-cccfb62c6133
ms.openlocfilehash: d4915526d5bb84b33f0595678781257d754aaf2d
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59024911"
---
# <a name="macros-and-c"></a>宏和 C++
C++ 提供新功能，其中一些取代了 ANSI C 预处理器提供的功能。 这些新功能可增强语言的类型安全性和可预见性：

- 在C++，对象声明为**const**可以在常量表达式中使用。 这使程序可以声明具有类型和值信息的常量，以及可以用调试器以符号方式查看的枚举。 使用预处理器 `#define` 指令定义常量不是那么精确。 没有存储分配给**const**对象，除非在程序中找到采用其地址的表达式。

- C++ 内联函数功能取代了函数类型宏。 使用内联函数取代宏的好处如下：

    - 类型安全。 内联函数需要接受与常规函数相同的类型检查。 宏不是类型安全。

    - 纠正具有副作用的参数的处理。 内联函数将计算在输入函数体前作为自变量提供的表达式。 因此，具有副作用的表达式不可能不安全。

内联函数的详细信息，请参阅[inline、 __inline、 \__forceinline](../cpp/inline-functions-cpp.md)。

出于向后兼容性的原因，将为 Microsoft C++ 保留存在于 ANSI C 以及更早的 C++ 规范中的所有预处理器工具。

## <a name="see-also"></a>请参阅

[预定义宏](../preprocessor/predefined-macros.md)<br/>
[宏 (C/C++)](../preprocessor/macros-c-cpp.md)