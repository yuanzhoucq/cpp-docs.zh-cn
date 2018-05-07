---
title: 编译器警告 （等级 1） C4399 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4399
dev_langs:
- C++
helpviewer_keywords:
- C4399
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b39f4919dd736e4bf2e6230fe68ea69c2b14766e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4399"></a>编译器警告（等级 1）C4399
symbol： 不应与使用 /clr 进行编译时 __declspec （dllimport） 标记为每个进程的符号： 纯  
  
 **/Clr: pure**编译器选项在 Visual Studio 2015 中已弃用。  
  
 本机映像或有本机和 CLR 构造的映像中的数据未导入到纯映像。 若要解决此警告，编译与 **/clr** (不 **/clr: pure**) 或删除`__declspec(dllimport)`。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4399。  
  
```  
// C4399.cpp  
// compile with: /clr:pure /doc /W1 /c  
__declspec(dllimport) __declspec(process) extern const int i;   // C4399  
```