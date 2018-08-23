---
title: nullptr |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- nullptr_cpp
dev_langs:
- C++
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 07e05e3a1c1b25e87053e15244f3c5fb9db442d9
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404156"
---
# <a name="nullptr"></a>nullptr
指定 `std::nullptr_t` 类型的 null 指针常量，该类型可转换为任何原始指针类型。  尽管可以使用关键字**nullptr**而不包含任何标头，如果您的代码使用类型`std::nullptr_t`，然后，必须通过包含标头定义它`<cstddef>`。  
  
> [!NOTE]
>  **Nullptr**关键字也是在 C + + /cli 适用于 CLI 托管代码应用程序和与 ISO 标准 c + + 关键字不可互换。 如果你的代码可能会通过编译[/clr](../build/reference/clr-common-language-runtime-compilation.md)编译器选项，以托管的代码为目标，然后使用`__nullptr`代码，必须保证编译器使用本机 C++ 解释的任何行中。 有关详细信息，请参阅[nullptr](../windows/nullptr-cpp-component-extensions.md)。  
  
## <a name="remarks"></a>备注  
 避免使用 NULL 或零 (`0`) 为 null 指针常量;**nullptr**是不易被误用，在大多数情况下更好地工作。  例如，给定 `func(std::pair<const char *, double>)`，那么调用 `func(std::make_pair(NULL, 3.14))` 会导致编译器错误。  宏 NULL 将扩展到 `0`，以便调用 `std::make_pair(0, 3.14)` 将返回 `std::pair<int, double>`，此结果不可转换为 func() 的 `std::pair<const char *, double>` 参数类型。  调用 `func(std::make_pair(nullptr, 3.14))` 将会成功编译，因为 `std::make_pair(nullptr, 3.14)` 返回 `std::pair<std::nullptr_t, double>`，此结果可转换为 `std::pair<const char *, double>`。  
  
## <a name="see-also"></a>请参阅  
 [关键字](../cpp/keywords-cpp.md)   
 [nullptr](../windows/nullptr-cpp-component-extensions.md)