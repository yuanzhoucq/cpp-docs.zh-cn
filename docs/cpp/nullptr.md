---
title: "nullptr |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- nullptr_cpp
- nullptr
dev_langs:
- C++
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 16bbbc38c61b2b6ff0539b2c71a0457b38465acb
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="nullptr"></a>nullptr
指定 `std::nullptr_t` 类型的 null 指针常量，该类型可转换为任何原始指针类型。  尽管您可以使用关键字 `nullptr` 而不包含任何标头，但如果您的代码使用类型 `std::nullptr_t`，则您必须通过包含标头 `<cstddef>` 来定义该类型。  
  
> [!NOTE]
>  用于托管代码应用程序的 C++/CLI 中也定义了 `nullptr` 关键字，并且它与 ISO 标准 C++ 关键字不可互换。 如果你的代码可能会通过编译[/clr](../build/reference/clr-common-language-runtime-compilation.md)编译器选项，以托管的代码为目标，然后使用`__nullptr`代码，必须保证编译器使用本机 c + + 解释的任何行中。 有关详细信息，请参阅[nullptr](../windows/nullptr-cpp-component-extensions.md)。  
  
## <a name="remarks"></a>备注  
 请避免将 `NULL` 或零 (`0`) 用作 null 指针常量；`nullptr` 不仅不易被误用，并且在大多数情况下使用效果更好。  例如，给定 `func(std::pair<const char *, double>)`，那么调用 `func(std::make_pair(NULL, 3.14))` 会导致编译器错误。  宏 NULL 将扩展到 `0`，以便调用 `std::make_pair(0, 3.14)` 将返回 `std::pair<int, double>`，此结果不可转换为 func() 的 `std::pair<const char *, double>` 参数类型。  调用 `func(std::make_pair(nullptr, 3.14))` 将会成功编译，因为 `std::make_pair(nullptr, 3.14)` 返回 `std::pair<std::nullptr_t, double>`，此结果可转换为 `std::pair<const char *, double>`。  
  
## <a name="see-also"></a>另请参阅  
 [关键字](../cpp/keywords-cpp.md)   
 [nullptr](../windows/nullptr-cpp-component-extensions.md)
