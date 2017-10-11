---
title: "编译器警告 C4368 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4368
dev_langs:
- C++
helpviewer_keywords:
- C4368
ms.assetid: cb85bcee-fd3d-4aa5-b626-2324f07a4f1b
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 6fd66d8fb6d30a960c659345910242ec5a1a2e11
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-warning-c4368"></a>编译器警告 C4368
不能定义为托管的 type 的成员 member： 不支持混合的类型  
  
 不能在 CLR 类型中嵌入的本机数据成员。  
  
 但是，您可以声明一个指向本机类型的指针，并在托管类的构造函数、析构函数和终结器中控制其生命周期。 有关详细信息请参阅[析构函数和终结器](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。  
  
 始终作为错误发出此警告。 使用[警告](../../preprocessor/warning.md)杂注来禁用 C4368。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4368。  
  
```  
// C4368.cpp  
// compile with: /clr /c  
struct N {};  
ref struct O {};  
ref struct R {  
    R() : m_p( new N ) {}  
    ~R() { delete m_p; }  
  
   property N prop;   // C4368  
   int i[10];   // C4368  
  
   property O ^ prop2;   // OK  
   N * m_p;   // OK  
};  
```
