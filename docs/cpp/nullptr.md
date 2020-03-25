---
title: nullptr
ms.date: 11/04/2016
f1_keywords:
- nullptr_cpp
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
ms.openlocfilehash: 223f4c3e8c838698f9716e241543db405c9394af
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177763"
---
# <a name="nullptr"></a>nullptr

指定 `std::nullptr_t` 类型的 null 指针常量，该类型可转换为任何原始指针类型。  尽管可以在不包含任何标头的情况下使用关键字**nullptr** ，但如果代码使用类型 `std::nullptr_t`，则必须通过包含标头 `<cstddef>`来定义该类型。

> [!NOTE]
>  **Nullptr**关键字还在/cli 中C++定义为托管代码应用程序，并且不能与 ISO 标准C++关键字互换。 如果你的代码可能使用[/clr](../build/reference/clr-common-language-runtime-compilation.md)编译器选项进行编译，该选项面向托管代码，则在任何代码行中使用 `__nullptr`，你必须确保编译器使用本机C++解释。 有关详细信息，请参阅[nullptr](../extensions/nullptr-cpp-component-extensions.md)。

## <a name="remarks"></a>备注

避免使用 NULL 或零（`0`）作为 NULL 指针常量;**nullptr**不太容易受到滥用的影响，并且在大多数情况下效果更佳。  例如，给定 `func(std::pair<const char *, double>)`，那么调用 `func(std::make_pair(NULL, 3.14))` 会导致编译器错误。  宏 NULL 将扩展到 `0`，以便调用 `std::make_pair(0, 3.14)` 将返回 `std::pair<int, double>`，此结果不可转换为 func() 的 `std::pair<const char *, double>` 参数类型。  调用 `func(std::make_pair(nullptr, 3.14))` 将会成功编译，因为 `std::make_pair(nullptr, 3.14)` 返回 `std::pair<std::nullptr_t, double>`，此结果可转换为 `std::pair<const char *, double>`。

## <a name="see-also"></a>另请参阅

[关键字](../cpp/keywords-cpp.md)<br/>
[nullptr](../extensions/nullptr-cpp-component-extensions.md)（C++/cli）
