---
title: "生存期 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- local variables, lifetime
- variables, automatic
- storage classes, lifetime
- variables, lifetime
- automatic storage class
- automatic storage class, duration
- storage class specifiers, storage duration
- memory allocation, dynamic allocation
- functions [C++], lifetime
- storage duration
- dynamic memory allocation
- memory allocation, dynamic
- lifetime
- global variables, lifetime
ms.assetid: ff0b42cb-3f0f-49a3-a94f-d1d825d8ddfe
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8ce98025001529313260f62e8f45e85add148c77
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="lifetime"></a>生存期
“生存期”是其中存在变量或函数的程序执行的时段。 标识符的存储持续时间决定其生存期。  
  
 使用 storage-class-specifier static 声明的标识符具有静态存储持续时间。 具有静态存储持续时间的标识符（也称为“全局”）具有存储和程序持续时间的定义值。 将保留存储，并且在程序启动前只将标识符的存储值初始化一次。 使用外部或内部链接声明的标识符还具有静态存储持续时间（请参阅[链接](../c-language/linkage.md)）。  
  
 如果在函数内部声明未使用 static 存储类说明符声明的标识符，则该标识符将具有自动存储持续时间。 具有自动存储持续时间的标识符（“本地标识符”）具有存储和已定义的值（仅在定义或声明该标识符的块中）。 程序每次进入该块时都将为自动标识符分配新存储，并在程序退出该块时丢失其存储（及其值）。 函数中声明的不具有链接的标识符也具有自动存储持续时间。  
  
 以下规则指定标识符是具有全局（静态）还是局部（自动）生存期：  
  
-   所有函数都具有静态生存期。 因此，它们在程序执行期间始终存在。 在外部级别（即，在同一级别函数定义的程序中的所有块之外）声明的标识符始终具有全局（静态）生存期。  
  
-   如果局部变量具有初始值设定项，则会在每次创建该变量时对其进行初始化（除非它被声明为 static）。 函数参数也具有本地生存期。 可以通过在标识符声明中包含 static 存储类说明符，在块中为该标识符指定全局生存期。 一旦声明 static，该变量会将其值从块中的一个项保留到下一个项中。  
  
 尽管源程序（例如，外部声明的变量或使用 static 关键字声明的局部变量）的执行中存在具有全局生存期的标识符，它也不会在程序的所有部分中可见。 有关可见性的信息，请参阅[范围和可见性](../c-language/scope-and-visibility.md)；有关 storage-class-specifier 非终止符的讨论，请参阅[存储类](../c-language/c-storage-classes.md)。  
  
 如果通过使用特殊库例程（如 `malloc`）创建，则可以根据需要分配内存（动态）。 由于动态内存分配使用库例程，因此它不被视为语言的一部分。 请参阅《运行时库参考》中的 [malloc](../c-runtime-library/reference/malloc.md) 函数。  
  
## <a name="see-also"></a>请参阅  
 [生存期、范围、可见性和链接](../c-language/lifetime-scope-visibility-and-linkage.md)