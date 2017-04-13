---
title: "编译器警告 （等级 4） C4634 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4634
dev_langs:
- C++
helpviewer_keywords:
- C4634
ms.assetid: 3e3496ce-2ac7-43d0-a48a-f514c950e81d
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: b08a4c0f716fe58ee9b5a2f3d54e1399c5848ee1
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-4-c4634"></a>编译器警告（等级 4）C4634
XML 文档注释：不能应用：原因  
  
 XML 文档标记不能应用于所有 C++ 构造。  例如，无法将文档注释添加到命名空间或模板中。  
  
 有关详细信息，请参阅[XML 文档](../../ide/xml-documentation-visual-cpp.md)。  
  
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
