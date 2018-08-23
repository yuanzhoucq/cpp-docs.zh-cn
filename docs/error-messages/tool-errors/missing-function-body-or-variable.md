---
title: 缺少函数体或变量 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- function body
- variables, missing
ms.assetid: 1a88d809-b14f-46a4-97c4-3e48beb418f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 54e2b8c5831eb6d487cf530df1b733b73580cbb8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33316720"
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
  
## <a name="see-also"></a>请参阅  
 [链接器工具错误 LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)