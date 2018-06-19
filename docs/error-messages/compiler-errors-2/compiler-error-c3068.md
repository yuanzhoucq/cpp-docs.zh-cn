---
title: 编译器错误 C3068 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3068
dev_langs:
- C++
helpviewer_keywords:
- C3068
ms.assetid: 613e3447-b4a8-4268-a661-297bed63ccdf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f378a60c79defed4fb1738515ca5b65b2851056
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256550"
---
# <a name="compiler-error-c3068"></a>编译器错误 C3068
function: naked 函数不能包含需要展开如果发生了 c + + 异常的对象  
  
 编译器无法执行堆栈展开上[裸](../../cpp/naked-cpp.md)函数引发了异常，因为临时对象的创建中的函数和 c + + 异常处理 ([/EHsc](../../build/reference/eh-exception-handling-model.md)) 指定。  
  
 若要解决此错误，请执行至少一个以下操作：  
  
-   使用 /EHsc 不编译。  
  
-   不要标记的功能与`naked`。  
  
-   函数中创建临时对象。  
  
 如果函数在堆栈中，创建临时对象，如果该函数将引发异常，并且启用 c + + 异常处理，编译器将清理堆栈如果引发异常。  
  
 当引发异常，编译器生成的代码，调用 prolog 和 epilog 和其中不存在的裸函数中时，将执行的函数。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3068:  
  
```  
// C3068.cpp  
// compile with: /EHsc  
// processor: x86  
class A {  
public:  
   A(){}  
   ~A(){}  
};  
  
void b(A){}  
  
__declspec(naked) void c() {  
   b(A());   // C3068   
};  
```