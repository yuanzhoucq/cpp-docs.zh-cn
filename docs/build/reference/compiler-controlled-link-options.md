---
title: "编译器控制的 LINK 选项 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- link
dev_langs:
- C++
helpviewer_keywords:
- LINK tool [C++], compiler-controlled options
- linker [C++], CL compiler control
- linking [C++], affected by CL features
- cl.exe compiler [C++], features that affect linking
- cl.exe compiler [C++], controlling linker
ms.assetid: e4c03896-c99c-4599-8502-e0f4bebe69d0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cc899fc7f1fc8c1805648e72e14ef13853841c90
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-controlled-link-options"></a>Compiler-Controlled LINK Options
除非另行指定，/c 选项，则 CL 编译器将自动调用链接。 CL 提供一定的控制链接器通过命令行选项和自变量。 下表汇总了 CL 影响链接的功能。  
  
|CL 规范|影响链接的 CL 操作|  
|----------------------|---------------------------------|  
|.C、.cxx、.cpp 或.def 以外任何文件扩展名|将文件名传递作为输入链接|  
|*filename*.def|将传递 /DEF:*filename*.def|  
|/F*数*|传递 /STACK:*数*|  
|/Fd*filename*|将传递 /PDB:*filename*|  
|/Fe*filename*|将传递 /out:*filename*|  
|/Fm*filename*|传递 /MAP:*filename*|  
|/Gy|创建打包的函数 (Comdat);启用函数级链接|  
|/LD|将传递 /DLL|  
|/LDd|将传递 /DLL|  
|/link|将命令行的其余部分传递给 LINK|  
|/MD 或 /MT|将默认库名放入.obj 文件|  
|/Mdd 或 /MTd|将默认库名放入.obj 文件中。 定义符号**_DEBUG**|  
|/nologo|将传递 /NOLOGO|  
|/Zd|传递 /DEBUG|  
|/Zi 或 /Z7|传递 /DEBUG|  
|/Zl|省略.obj 文件中的默认库名称|  
  
 有关详细信息，请参阅[编译器选项](../../build/reference/compiler-options.md)。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)