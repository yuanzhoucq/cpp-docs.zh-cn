---
title: 编译器警告 （等级 4） C4634 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4634
dev_langs:
- C++
helpviewer_keywords:
- C4634
ms.assetid: 3e3496ce-2ac7-43d0-a48a-f514c950e81d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7b19a4d0cbbb7b2b8fce0035698add596a445d3c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299765"
---
# <a name="compiler-warning-level-4-c4634"></a>编译器警告（等级 4）C4634
XML 文档注释：不能应用：原因  
  
 XML 文档标记不能应用于所有 C++ 构造。  例如，无法将文档注释添加到命名空间或模板中。  
  
 有关更多信息，请参见 [XML Documentation](../../ide/xml-documentation-visual-cpp.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4634。  
  
```  
// C4634.cpp  
// compile with: /W4 /doc /c  
/// This is a namespace.   // C4634  
namespace hello {  
   class MyClass  {};  
};  
```  
  
## <a name="example"></a>示例  
 下面的示例生成 C4634。  
  
```  
// C4634_b.cpp  
// compile with: /W4 /doc /c  
/// This is a template.   // C4634  
template <class T>  
class MyClass  {};  
```