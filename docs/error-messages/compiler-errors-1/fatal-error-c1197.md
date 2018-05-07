---
title: 错误 C1197 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1197
dev_langs:
- C++
helpviewer_keywords:
- C1197
ms.assetid: 22b801b7-e792-41f6-a461-973c03c69f25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dacd459729161cf635287697a4a6d35c15eab3e4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1197"></a>错误 C1197
不能引用 mscorlib.dll_1，因为程序已经引用 mscorlib.dll_2  
  
 编译器符合公共语言运行时的版本。  但是，已尝试从早期版本中引用的公共语言运行时文件的版本。  
  
 若要解决此错误，只能引用与编译所用的 Visual c + + 版本附带的公共语言运行时版本中的文件。  
  
## <a name="example"></a>示例  
 下面的示例生成 C1197:  
  
```  
// C1197.cpp  
// compile with: /clr /c  
// processor: x86  
#using "C:\Windows\Microsoft.NET\Framework\v1.1.4322\mscorlib.dll"   // C1197  
// try the following line instead  
// #using "mscorlib.dll"  
```