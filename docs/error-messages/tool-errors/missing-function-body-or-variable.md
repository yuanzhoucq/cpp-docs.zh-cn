---
title: "缺少函数体或变量 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
dev_langs: C++
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ba591b6bba935ff5ee6669dd0feb62fb9bd05177
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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