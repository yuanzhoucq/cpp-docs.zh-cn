---
title: 编译器警告 （等级 3） C4641 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4641
dev_langs:
- C++
helpviewer_keywords:
- C4641
ms.assetid: 28fe5c3e-6039-42da-9100-1312b5b15aea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ea8413971353e7ffbe6579412d0eed9c735b91b0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4641"></a>编译器警告（等级 3）C4641
XML 文档注释含有不明确的交叉引用。  
  
 编译器无法明确地解析的引用。 若要解决此警告，请指定明确引用所需的参数信息。  
  
 有关更多信息，请参见 [XML Documentation](../../ide/xml-documentation-visual-cpp.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4641。  
  
```  
// C4641.cpp  
// compile with: /W3 /doc /clr /c  
  
/// <see cref="f" />   // C4641  
// try the following line instead  
// /// <see cref="f(int)" />  
public ref class GR {  
public:  
   void f( int ) {}  
   void f( char ) {}  
};  
```