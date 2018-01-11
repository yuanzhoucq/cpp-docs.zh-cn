---
title: "编译器警告 （等级 4） C4564 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4564
dev_langs: C++
helpviewer_keywords: C4564
ms.assetid: 555b301b-313e-4262-9f81-eb878674be60
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 25f9f8755acafd71a9ac75a68f601660b781746a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4564"></a>编译器警告（等级 4）C4564
方法 method 类 class 的定义不支持的默认参数 parameter  
  
 编译器检测到具有使用默认值的一个或多个参数的方法。 调用方法; 时，将忽略参数的默认值显式指定这些参数的值。 如果不显式指定这些参数的值，c + + 编译器将生成错误。  
  
 给定的 Visual Basic 创建以下.dll 文件的情况下，这允许默认参数上的方法自变量：  
  
```  
' C4564.vb  
' compile with: vbc /t:library C4564.vb  
Public class TestClass  
   Public Sub MyMethod (a as Integer, _  
                        Optional c as Integer=1)  
   End Sub  
End class  
```  
  
 和下面的 c + + 示例使用.dll 使用 Visual Basic 中，创建  
  
```  
// C4564.cpp  
// compile with: /clr /W4 /WX  
#using <C4564.dll>  
  
int main() {  
   TestClass ^ myx = gcnew TestClass();   // C4564  
   myx->MyMethod(9);  
   // try the following line instead, to avoid an error  
   // myx->MyMethod(9, 1);  
}  
```