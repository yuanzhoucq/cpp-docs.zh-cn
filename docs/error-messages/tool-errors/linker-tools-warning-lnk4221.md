---
title: "链接器工具警告 LNK4221 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4221"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4221"
ms.assetid: 8e2eb2de-9532-4b85-908a-8c9ff5c4cccb
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 链接器工具警告 LNK4221
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此对象文件未定义任何之前未定义的公共符号，因此任何耗用此库的链接操作都不会使用此文件  
  
 请考虑下面的两个代码段。  
  
```  
// a.cpp  
#include <atlbase.h>  
```  
  
```  
// b.cpp  
#include <atlbase.h>  
int function()  
{  
   return 0;  
}  
  
```  
  
 若要编译文件并创建两个对象文件，请在命令提示上运行 **cl \/c a.cpp b.cpp**。  如果通过运行 **link \/lib \/out:test.lib a.obj b.obj** 来链接对象文件，将会接收到 LNK4221 警告。  如果通过运行 **link \/lib \/out:test.lib b.obj a.obj** 来链接对象，则不会接收到警告。  
  
 因为链接器按照后进先出 \(LIFO\) 的方式操作，所以在第二个方案中未发出警告。  在第一个方案中，b.obj 在 a.obj 之前进行处理，而 a.obj 没有要添加的新符号。  通过指示链接器首先处理 a.obj，可以避免出现警告。  
  
 此错误的一个常见原因是，两个源文件使用在**“预编译头”**字段中指定的相同头文件名称指定选项 [\/Yc（创建预编译的头文件）](../../build/reference/yc-create-precompiled-header-file.md)。  此问题的一个常见原因涉及 stdafx.h，因为默认情况下 stdafx.cpp 包含 stdafx.h 并且不添加任何新符号。  如果另一个源文件使用 **\/Yc** 来包含 stdafx.h，并且在 stdafx.obj 之前处理关联的 .obj 文件，则链接器将引发 LNK4221。  
  
 解决此问题的一种方法是：对于每个预编译的头，确保只有一个源文件使用 **\/Yc** 包含它。  所有其他源文件必须使用预编译头。  有关如何更改此设置的更多信息，请参见 [\/Yu（使用预编译的头文件）](../../build/reference/yu-use-precompiled-header-file.md)。