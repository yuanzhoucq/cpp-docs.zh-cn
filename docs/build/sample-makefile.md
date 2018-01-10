---
title: "示例生成文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 8343ce71-5556-4ae0-8d1e-7efd82673070
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7559926b622d3b844107daffd9a52ab4f2402604
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="sample-makefile"></a>示例生成文件
本主题包含示例生成文件。  
  
## <a name="sample"></a>示例  
  
### <a name="code"></a>代码  
  
```  
# Sample makefile  
  
!include <win32.mak>  
  
all: simple.exe challeng.exe  
  
.c.obj:  
  $(cc) $(cdebug) $(cflags) $(cvars) $*.c  
  
simple.exe: simple.obj  
  $(link) $(ldebug) $(conflags) -out:simple.exe simple.obj $(conlibs) lsapi32.lib  
  
challeng.exe: challeng.obj md4c.obj  
  $(link) $(ldebug) $(conflags) -out:challeng.exe $** $(conlibs) lsapi32.lib  
```  
  
## <a name="see-also"></a>请参阅  
 [生成文件的内容](../build/contents-of-a-makefile.md)