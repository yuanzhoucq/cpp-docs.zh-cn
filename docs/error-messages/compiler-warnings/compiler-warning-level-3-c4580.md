---
title: "编译器警告 （等级 3） C4580 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4580
dev_langs:
- C++
helpviewer_keywords:
- C4580
ms.assetid: fef6e8e0-0d6a-44fa-b22a-2fe7ba2ef379
caps.latest.revision: 8
author: corob-msft
ms.author: corob
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: b551b1a7e0ae03a7de5108a1d114155786972847
ms.openlocfilehash: c8cebbda1d3472a2efda43f816e7a13f2f460408
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-3-c4580"></a>编译器警告（等级 3）C4580
[attribute] 已弃用；改为指定 System::Attribute 或 Platform::Metadata 作为基类  
  
[[属性](../../windows/attribute.md)] 不再用于创建用户定义的特性的首选的语法。 有关详细信息，请参阅[用户定义属性](../../windows/user-defined-attributes-cpp-component-extensions.md)。 对于 CLR 代码，请从 `System::Attribute` 派生特性。 对于 Windows 运行时代码，请从 `Platform::Metadata` 派生特性。  
  
## <a name="example"></a>示例  
下面的示例将生成 C3454，并演示如何修复此错误。  
  
```cpp  
// C4580.cpp  
// compile with: /W3 /c /clr  
[attribute]   // C4580  
public ref class Attr {  
public:  
   int m_t;  
};  
  
public ref class Attr2 : System::Attribute {  
public:  
   int m_t;  
};  
```
