---
title: "C 扩展的存储类特性 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C]
- extended attributes
- extended storage-class attributes
- storage class specifiers, C storage classes
ms.assetid: 2580735c-f5bf-46ab-9468-0696893d82be
caps.latest.revision: 9
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
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: e79b08ebba48221e8666ced75875a68f06bf2df3
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

---
# <a name="c-extended-storage-class-attributes"></a>C 扩展的存储类特性
**Microsoft 专用**  
  
 有关本主题的更多最新信息可以在 [__declspec（C++ 参考）](../cpp/declspec.md)下找到。  
  
 扩展的特性语法简化并标准化了特定于 Microsoft 的 C 语言扩展。 使用扩展的特性语法的存储类特性包括 thread、naked、dllimport 和 dllexport。  
  
 用于指定存储类信息的扩展特性语法使用 __declspec 关键字，这指定给定类型的实例将与特定于 Microsoft 的存储类特性（thread、naked、dllimport 或 dllexport）一起存储。 其他存储类修饰符的示例包括 static 和 extern 关键字。 但是，这些关键字是 ANSI C 标准的一部分，因此未涵盖在扩展的特性语法中。  
  
## <a name="syntax"></a>语法  
 *storage-class-specifier*：  
 `__declspec` ( extended-decl-modifier-seq ) /* Microsoft 专用 \*/  
  
 extended-decl-modifier-seq：  
extended-decl-modifier ** opt  
  
 *extended-decl-modifier-seq extended-decl-modifier*  
  
 extended-decl-modifier：  
 **thread**  
  
 **naked**  
  
 **dllimport**  
  
 `dllexport`  
  
 空格可分隔声明修饰符。 请注意，extended-decl-modifier-seq 可以为空；在此情况下，__declspec 不起作用。  
  
 thread、naked、dllimport 和 dllexport 存储类特性仅为它们应用于的数据或函数的声明的属性；它们不重新定义函数自身的类型特性。 thread 特性只影响数据。 naked 特性仅影响函数。 dllimport 和 dllexport 特性影响函数和数据。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [声明和类型](../c-language/declarations-and-types.md)
