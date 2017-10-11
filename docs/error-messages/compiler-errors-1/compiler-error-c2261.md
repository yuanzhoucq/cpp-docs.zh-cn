---
title: "编译器错误 C2261 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2261
dev_langs:
- C++
helpviewer_keywords:
- C2261
ms.assetid: 60969482-9e83-49b5-9631-a04bc844da12
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 8269b891ed899501625973b81c1823d4db2d56c8
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2261"></a>编译器错误 C2261
'string': 程序集引用无效，无法解析  
  
 值不是有效的。  
  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>用于指定友元程序集。 例如，如果 a.dll 想要指定 b.dll 为友元程序集，你会指定 （在 a.dll): InternalsVisibleTo("b")。 然后，运行时允许 b.dll 访问 a.dll （除外私有类型） 中的所有内容。  
  
 有关指定友元程序集时，正确的语法的详细信息，请参阅[友元程序集 （c + +）](../../dotnet/friend-assemblies-cpp.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2261。  
  
```  
// C2261.cpp  
// compile with: /clr /c  
using namespace System::Runtime::CompilerServices;  
[assembly: InternalsVisibleTo("a,a,a")];   // C2261  
[assembly: InternalsVisibleTo("a.a")];   // OK  
[assembly: InternalsVisibleTo("a")];   // OK  
```
