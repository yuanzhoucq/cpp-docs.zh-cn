---
title: "存储类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- linkage [C++], external
- function storage class
- function specifiers, storage class
- storage classes
- Microsoft-specific storage classes
- external linkage, storage-class specifiers
- static storage class specifiers
ms.assetid: 39a79ba6-edf5-42b6-8e45-f94227603dd6
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a4385515becbb32b256b2bf6562af941371ef47e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="storage-class"></a>存储类
函数定义中的存储类说明符为函数提供 `extern` 或 static 存储类。  
  
## <a name="syntax"></a>语法  
 function-definition：  
 declaration-specifiers optattribute-seq optdeclarator declaration-list optcompound-statement  
  
 /\* *attribute-seq* 为 Microsoft 专用 */  
  
 *declaration-specifiers*：  
 storage-class-specifier declaration-specifiers opt  
  
 type-specifier declaration-specifiers opt  
  
 type-qualifier declaration-specifiers opt  
  
 storage-class-specifier: /\* 针对函数定义 \*/  
 **extern**  
  
 **static**  
  
 如果函数定义不包括 storage-class-specifier，则存储类默认为 `extern`。 您可以将函数显式声明为 `extern`，但这不是必需的。  
  
 如果函数的声明包含 storage-class-specifier `extern`，则标识符拥有与带文件范围的标识符的任何可见声明相同的链接。 如果没有带文件范围的可见声明，则标识符具有外部链接。 如果标识符具有文件范围但没有 storage-class-specifier，则标识符具有外部链接。 外部链接意味着，标识符的每个实例表示相同的对象或函数。 有关链接和文件范围的详细信息，请参阅[生存期、范围、可见性和链接](../c-language/lifetime-scope-visibility-and-linkage.md)。  
  
 带 `extern` 之外的存储类说明符的块范围数声明将生成错误。  
  
 带 static 存储类的函数仅在定义它的源文件中可见。 所有其他函数（无论是显式还是隐式地为它们提供 `extern` 存储类）在程序中的所有源文件中都可见。 如果需要 static 存储类，则必须在函数声明（如果有）的第一个匹配项和函数定义中声明该存储类。  
  
 **Microsoft 专用**  
  
 在启用 Microsoft 扩展时，如果函数定义在同一源文件中且定义显式指定 static 存储类，则会为最初未使用存储类（或使用 `extern` 存储类）声明的函数提供 static 存储类。  
  
 当使用 /Ze 编译器选项进行编译时，使用 `extern` 关键字在块内声明的函数具有全局可见性。 在使用 /Za 编译时，并非如此。 如果需要考虑源代码的可移植性，则不应依赖此功能。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [C 函数定义](../c-language/c-function-definitions.md)