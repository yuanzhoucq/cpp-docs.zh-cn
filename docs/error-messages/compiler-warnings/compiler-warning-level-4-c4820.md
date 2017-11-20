---
title: "编译器警告 （等级 4） C4820 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4820
dev_langs: C++
helpviewer_keywords: C4820
ms.assetid: 17aa29f4-c287-49b8-bc43-8ed82ffed5ea
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5af422ff96778435c56ff3497d50fb7e923b2297
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4820"></a>编译器警告（等级 4）C4820
“bytes”字节填充添加在构造“member_name”之后  
  
 类型和元素的顺序导致编译器将填充添加到结构末尾。 请参阅[对齐](../../cpp/align-cpp.md)有关填充在结构中的详细信息。  
  
 默认情况下，此警告处于关闭状态。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。  
  
 下面的示例生成 C4820:  
  
```  
// C4820.cpp  
// compile with: /W4 /c  
#pragma warning(default : 4820)   
  
// Delete the following 4 lines to resolve.  
__declspec(align(2)) struct MyStruct {  
   char a;  
   int i;   // C4820  
};  
  
// OK  
#pragma pack(1)  
__declspec(align(1)) struct MyStruct2 {  
   char a;  
   int i;  
};  
```