---
title: 链接器工具警告 LNK4247 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4247
dev_langs:
- C++
helpviewer_keywords:
- LNK4247
ms.assetid: 085d7fdf-9eaf-4641-8473-6eaadd073c7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6096bbfba9c60d8ed28aa660d078cd155f0316a3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301198"
---
# <a name="linker-tools-warning-lnk4247"></a>链接器工具警告 LNK4247
入口点 decorated_function_name 已有的线程特性;attribute 忽略  
  
 使用指定的入口点[/ENTRY （入口点符号）](../../build/reference/entry-entry-point-symbol.md)，有线程处理的属性，但[/CLRTHREADATTRIBUTE （设置 CLR 线程特性）](../../build/reference/clrthreadattribute-set-clr-thread-attribute.md)还被指定，使用不同的线程处理模型。  
  
 链接器忽略 /CLRTHREADATTRIBUTE 用指定的值。  
  
 若要解决此警告：  
  
-   从你的生成删除 /CLRTHREADATTRIBUTE。  
  
-   从源代码文件中删除属性。  
  
-   从你的生成，从源和 /CLRTHREADATTRIBUTE 删除这两个属性，并接受默认 CLR 线程处理模型。  
  
-   更改传递给 /CLRTHREADATTRIBUTE 的值，以便它与源中的属性。  
  
-   更改源中的属性，以便它与传递给 /CLRTHREADATTRIBUTE 的值一致。  
  
 下面的示例生成 LNK4247  
  
```  
// LNK4247.cpp  
// compile with: /clr /c  
// post-build command: link /CLRTHREADATTRIBUTE:STA LNK4247.obj /entry:functionTitle /SUBSYSTEM:Console  
 [System::MTAThreadAttribute]  
void functionTitle (){}  
```