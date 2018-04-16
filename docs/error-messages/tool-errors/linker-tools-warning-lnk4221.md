---
title: "链接器工具警告 LNK4221 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4221
dev_langs:
- C++
helpviewer_keywords:
- LNK4221
ms.assetid: 8e2eb2de-9532-4b85-908a-8c9ff5c4cccb
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a3fb348ebb05b7af40821b4f3968a920c2e9e773
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4221"></a>链接器工具警告 LNK4221
此对象文件未定义任何以前未定义的公共符号，因此它不使用通过使用此库的任何链接操作  
  
 请考虑以下两个代码段。  
  
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
  
 若要编译文件并创建两个对象文件，运行**cl /c a.cpp b.cpp**在命令提示符。 如果你通过运行链接对象文件**链接/lib /out:test.lib a.obj b.obj**，你将收到 LNK4221 警告。 如果将对象链接通过运行**链接/lib /out:test.lib b.obj a.obj**，你将不会收到一条警告。  
  
 在第二个方案中会不发出任何警告，因为链接器会在后进先出 (LIFO) 方式运行。 在第一个方案中之前 a.obj，处理 b.obj 和 a.obj 已添加任何新符号。 指示链接器首先处理 a.obj，可以避免此警告。  
  
 此错误的常见原因是当两个源文件指定选项[/Yc （创建预编译标头文件）](../../build/reference/yc-create-precompiled-header-file.md)同名标头文件中指定**预编译标头**字段。 由于默认情况下，stdafx.cpp 包括 stdafx.h 并不会添加任何新符号，导致此问题的常见原因涉及到 stdafx.h。 如果另一个源文件中包含与 stdafx.h **/Yc**和之前 stdafx.obj 处理关联的.obj 文件，则链接器将引发 LNK4221。  
  
 一种方法要解决此问题是确保对于每个预编译标头，没有只有一个源文件包含与它的**/Yc**。 所有其他源文件必须使用预编译标头。 有关如何更改此设置的详细信息，请参阅[/Yu （使用预编译标头文件）](../../build/reference/yu-use-precompiled-header-file.md)。