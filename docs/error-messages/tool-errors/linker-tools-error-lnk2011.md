---
title: 链接器工具错误 LNK2011 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2011
dev_langs:
- C++
helpviewer_keywords:
- LNK2011
ms.assetid: 04991ef5-49d5-46c7-8eee-a9d1d3fc541e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f60dce4cb260c670f5ee82aa88b9f106f3f14e2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk2011"></a>链接器工具错误 LNK2011
预编译的对象中; 不链接图像可能无法运行  
  
 如果你使用预编译标头，链接要求的所有对象文件使用预编译标头创建必须链接到。 如果你有一个源文件，则使用与其他源文件生成使用的预编译标头，你现在必须包含预编译标头以及创建的对象文件。  
  
 例如，如果编译 stub.cpp 使用其他源文件中创建的预编译标头，使用的文件，必须与 STUB.obj 链接，或将发生此错误。 在下面的命令行中，一个用于创建预编译标头，COMMON.pch，在两个和第三行中与 PROG1.cpp 和 PROG2.cpp 一起使用。 STUB.cpp 只包含文件`#include`行 (相同`#include`线如下所示 PROG1.cpp 和 PROG2.cpp) 和仅用于生成预编译标头。 在最后一个行中，STUB.obj 必须链接到以免 LNK2011。  
  
```  
cl /c /Yccommon.h stub.cpp  
cl /c /Yucommon.h prog1.cpp  
cl /c /Yucommon.h prog2.cpp  
link /out:prog.exe stub.obj prog1.obj prog2.obj  
```