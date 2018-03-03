---
title: "编译器警告 （等级 3） C4398 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4398
dev_langs:
- C++
helpviewer_keywords:
- C4398
ms.assetid: b6221432-9fed-4272-a547-a73f587904e6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d5ce6355e50c1ea2594820388edc34c69ea0e899
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4398"></a>编译器警告（等级 3）C4398
variable： 每个进程的全局对象可能无法正确使用多个 appdomain;请考虑使用 __declspec(appdomain)  
  
 具有虚拟函数[__clrcall](../../cpp/clrcall.md)本机类型中调用约定将导致创建每个应用程序域 vtable。 在多个应用程序域中使用时，可能无法正确解决此类变量。  
  
 通过显式标记变量就可以解决此警告`__declspec(appdomain)`。 在 Visual Studio 2017 之前的 Visual Studio 版本中，则可以通过使用进行编译解决此警告**/clr: pure**，默认情况下生成每个 appdomain 的全局变量。  
  
 有关详细信息，请参阅[appdomain](../../cpp/appdomain.md)和[应用程序域和 Visual c + +](../../dotnet/application-domains-and-visual-cpp.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4398。  
  
```  
// C4398.cpp  
// compile with: /clr /W3 /c  
struct S {  
   virtual void f( System::String ^ );   // String^ parameter makes function __clrcall  
};  
  
S glob_s;   // C4398  
__declspec(appdomain) S glob_s2;   // OK  
```