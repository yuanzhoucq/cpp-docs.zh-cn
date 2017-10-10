---
title: "编译器错误 C2393 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2393
dev_langs:
- C++
helpviewer_keywords:
- C2393
ms.assetid: 4bd95728-e813-4ce8-844a-c6ebe235ca82
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: a2c4f8d31fb6ddb6eaa9472dc7537edbcdc29054
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2393"></a>编译器错误 C2393
symbol： 不能在段领域中分配每个 appdomain 符号  
  
 **/clr:pure** 和 **/clr:safe** 编译器选项在 Visual Studio 2015 中已弃用。  
  
 使用[appdomain](../../cpp/appdomain.md)变量表示您正在用编译**/clr: pure**或**/clr: safe**，和的安全或纯映像不能包含数据段。  
  
 请参阅[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)有关详细信息。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2393。  
  
```  
// C2393.cpp  
// compile with: /clr:pure /c  
#pragma data_seg("myseg")  
int n = 0;   // C2393  
```
