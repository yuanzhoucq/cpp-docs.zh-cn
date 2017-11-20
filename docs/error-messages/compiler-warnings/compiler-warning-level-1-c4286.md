---
title: "编译器警告 （等级 1） C4286 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4286
dev_langs: C++
helpviewer_keywords: C4286
ms.assetid: 93eadd6c-6f36-413b-ba91-c9aa2314685a
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 71abc86a66f08cbdceb422b74fa5ca600b110a0f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4286"></a>编译器警告（等级 1）C4286
type1： 由基类 (type2) 在行号上捕获  
  
 指定的异常类型由上一个处理程序处理。 第二个 catch 的类型派生自的第一个类型。 异常的基类捕获异常的派生类。  
  
## <a name="example"></a>示例  
  
```  
//C4286.cpp  
// compile with: /W1  
#include <eh.h>  
class C {};  
class D : public  C {};  
int main()  
{  
    try  
    {  
        throw "ooops!";  
    }  
    catch( C ) {}  
    catch( D ) {}  // warning C4286, D is derived from C  
}  
```