---
title: 编译器警告 （等级 3） C4580 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4580
dev_langs:
- C++
helpviewer_keywords:
- C4580
ms.assetid: fef6e8e0-0d6a-44fa-b22a-2fe7ba2ef379
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 89ad08af77b62cd0992e9415e2df8b31233e4e0d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4580"></a>编译器警告（等级 3）C4580
[attribute] 已弃用；改为指定 System::Attribute 或 Platform::Metadata 作为基类  
  
[[属性](../../windows/attribute.md)] 不再是创建用户定义的特性的首选的语法。 有关详细信息，请参阅 [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md)。 对于 CLR 代码，请从 `System::Attribute` 派生特性。 对于 Windows 运行时代码，请从 `Platform::Metadata` 派生特性。  
  
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