---
title: nullptr
ms.date: 11/04/2016
f1_keywords:
- nullptr_cpp
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
ms.openlocfilehash: 51df20ea00e5dd77ab1fc1a2a01253b8f788ad0a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358844"
---
# <a name="nullptr"></a>nullptr

指定 `std::nullptr_t` 类型的 null 指针常量，该类型可转换为任何原始指针类型。  尽管可以使用关键字**nullptr**而不包括任何标头，但如果代码使用 类型`std::nullptr_t`，则必须通过包括标头`<cstddef>`来定义它。

> [!NOTE]
> **nullptr**关键字也C++/CLI 中为托管代码应用程序定义，不能与 ISO 标准C++关键字互换。 如果代码可能使用以托管代码为目标的[/clr](../build/reference/clr-common-language-runtime-compilation.md)编译器选项进行编译，则在任何`__nullptr`代码行中使用，其中必须保证编译器使用本机C++解释。 有关详细信息，请参阅[nullptr](../extensions/nullptr-cpp-component-extensions.md)。

## <a name="remarks"></a>备注

避免使用 NULL 或`0`零 （ ） 作为空指针常量;**在大多数情况下，空位**不易被误用，效果更好。  例如，给定 `func(std::pair<const char *, double>)`，那么调用 `func(std::make_pair(NULL, 3.14))` 会导致编译器错误。  宏 NULL 将扩展到 `0`，以便调用 `std::make_pair(0, 3.14)` 将返回 `std::pair<int, double>`，此结果不可转换为 func() 的 `std::pair<const char *, double>` 参数类型。  调用 `func(std::make_pair(nullptr, 3.14))` 将会成功编译，因为 `std::make_pair(nullptr, 3.14)` 返回 `std::pair<std::nullptr_t, double>`，此结果可转换为 `std::pair<const char *, double>`。

## <a name="see-also"></a>另请参阅

[Keywords](../cpp/keywords-cpp.md)<br/>
[空值](../extensions/nullptr-cpp-component-extensions.md)（C++/CLI）
