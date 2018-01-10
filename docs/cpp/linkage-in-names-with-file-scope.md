---
title: "带文件范围的名称中的链接 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- scope [C++], linkage rules
- linkage [C++], scope linkage rules
- names [C++], scope linkage rules
- static modifier, file scope
- static names and file scope
- file scope [C++]
- declarations [C++], external
- external linkage, scope linkage rules
- static variables, external declarations
ms.assetid: 38d3fa5e-1861-466e-a590-84b86f7b184e
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 581d7798f4f3aaa409d843f8b7f3b5869b47407e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linkage-in-names-with-file-scope"></a>具有文件范围的名称中的链接
以下链接规则适用于带文件范围的名称（`typedef` 和枚举器名称除外）：  
  
-   如果将名称显式声明为**静态**，它具有内部链接并标识其自己的翻译单元中的程序元素。  
  
-   枚举器名称和 `typedef` 名称没有链接。  
  
-   带文件范围的所有其他名称都具有外部链接。  
  
 **Microsoft 专用**  
  
-   如果带文件范围的函数名称显式声明为**内联**，如果它实例化或引用其地址时，它具有外部链接。 因此，带文件范围的函数可以拥有内部链接或外部链接。  
  
 **结束 Microsoft 专用**  
  
 在以下情况下，类具有内部链接：  
  
-   不使用 C++ 功能（例如，成员访问控制、成员函数、构造函数、析构函数等）。  
  
-   未用于具有外部链接的另一个名称的声明中。 此约束意味着，传递到带外部链接的函数的类类型对象会导致该类具有外部链接。  
  
## <a name="see-also"></a>请参阅  
 [程序和链接](../cpp/program-and-linkage-cpp.md)