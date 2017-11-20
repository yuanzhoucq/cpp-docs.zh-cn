---
title: "错误 C1197 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1197
dev_langs: C++
helpviewer_keywords: C1197
ms.assetid: 22b801b7-e792-41f6-a461-973c03c69f25
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d0eb3ab152e9299d47210a6d2c1eb58e3f92a925
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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