---
title: "缺少函数体或变量 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
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
ms.sourcegitcommit: 4bac7b2942f9d72674b8092dc7bf64174dd3c349
ms.openlocfilehash: c80a5626e7f674ddca7d44e94aa8ab64c735c81e
ms.contentlocale: zh-cn
ms.lasthandoff: 04/24/2017

---
# <a name="missing-function-body-or-variable"></a>缺少函数体或变量
只有函数原型，编译器可以继续未生成错误，但链接器无法解析为地址的调用，因为没有函数代码或变量保留的空间。 在创建链接器必须解析的函数调用之前，不会看到此错误。  
  
## <a name="example"></a>示例  
 在 main 中的函数调用将会导致 LNK2019，因为该原型会使编译器认为存在的函数。  链接器查找它不会。  
  
```  
// LNK2019_MFBV.cpp  
// LNK2019 expected  
void DoSomething(void);  
int main() {  
   DoSomething();  
}  
```  
  
## <a name="example"></a>示例  
 在 c + +，请确保类定义中包括的一个类而不只是原型的特定函数的实现。 如果你正在定义标头文件外部的类，请务必包括在该函数前的类名称 (`Classname::memberfunction`)。  
  
```  
// LNK2019_MFBV_2.cpp  
// LNK2019 expected  
struct A {  
   static void Test();  
};  
  
// Should be void A::Test() {}  
void Test() {}  
  
int main() {  
   A AObject;  
   AObject.Test();  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [链接器工具错误 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)
