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
caps.latest.revision: 6
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
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 18270bb89bcc5d1855750c572a5b6fb9e51c2ba3
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-3-c4398"></a>编译器警告（等级 3）C4398
variable︰ 每个进程的全局对象可能无法正常运行多个 appdomain;请考虑使用 __declspec(appdomain)  
  
 具有虚函数[__clrcall](../../cpp/clrcall.md)本机类型中调用约定将导致创建每个应用程序域 vtable。 多个应用程序域中使用时，可能无法正确地解决此类变量。  
  
 可以通过显式标记变量来解决此警告`__declspec(appdomain)`。 在 Visual Studio 2017 之前的 Visual Studio 版本中，您可以通过使用进行编译会解决此警告**/clr: pure**，默认情况下生成每个 appdomain 的全局变量。  
  
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
