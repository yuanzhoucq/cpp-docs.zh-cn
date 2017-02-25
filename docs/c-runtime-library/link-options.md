---
title: "链接选项 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "nothrownew.obj"
  - "newmode.obj"
  - "noenv.obj"
  - "psetargv.obj"
  - "loosefpmath.obj"
  - "smallheap.obj"
  - "fp10.obj"
  - "nochkclr.obj"
  - "chkstk.obj"
  - "pcommode.obj"
  - "pnoenv.obj"
  - "链接选项 [C++]"
  - "invalidcontinue.obj"
  - "pnothrownew.obj"
  - "pwsetargv.obj"
  - "pinvalidcontinue.obj"
  - "wsetargv.obj"
  - "binmode.obj"
  - "setargv.obj"
  - "noarg.obj"
  - "pnewmode.obj"
  - "commode.obj"
  - "pthreadlocale.obj"
  - "pbinmode.obj"
  - "threadlocale.obj"
  - "pnoarg.obj"
ms.assetid: 05b5a77b-9dd1-494b-ae46-314598c770bb
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 链接选项
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

CRT lib 目录包括一些小的对象文件，用于指定CRT的功能而不改变代码。  因为只须将他们添加到链接器命令行使用它们，这些调用链接选项。  
  
 纯模式版本添加了。  对为本地 \/clr 代码使用普通版本，为\/clr:纯净模式使用纯净版本（前缀为p）。  
  
|本机的和 \/clr|纯模式|说明|  
|----------------|---------|--------|  
|binmode.obj|pbinmode.obj|设置默认文件转换模式为二进制。  请参见[\_fmode](../c-runtime-library/fmode.md)。|  
|chkstk.obj|无|不使用CRT时，提供堆栈检查和alloca支持。|  
|commode.obj|pcommode.obj|设置全局提交标志为“提交”。  请参见[fopen、\_wfopen](../c-runtime-library/reference/fopen-wfopen.md)和[fopen\_s、\_wfopen\_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)。|  
|fp10.obj|无|更改默认精度控件为64位。  请参见[浮点支持](../c-runtime-library/floating-point-support.md)。|  
|invalidcontinue.obj|pinvalidcontinue.obj|设置默认的无效参数处理程序将不执行任何操作的，这意味着无效参数传递到 CRT 函数将设置 errno 并返回错误结果。|  
|loosefpmath.obj|无|确保浮点代码可以接受非正规值。|  
|newmode.obj|pnewmode.obj|引起[malloc](../c-runtime-library/reference/malloc.md)在错误的调用新的处理句柄。  请参见 [\_set\_new\_mode](../c-runtime-library/reference/set-new-mode.md)、[\_set\_new\_handler](../c-runtime-library/reference/set-new-handler.md)、[calloc](../c-runtime-library/reference/calloc.md) 和 [realloc](../c-runtime-library/reference/realloc.md)。|  
|noarg.obj|pnoarg.obj|禁用处理所有argc和argv。|  
|nochkclr.obj|无|不做任何操作。  从项目中移除。|  
|noenv.obj|pnoenv.obj|禁用CRT的缓存环境的创建。|  
|nothrownew.obj|pnothrownew.obj|启用CRT新的不抛出异常版本。  请参见[new 和 delete 运算符](../cpp/new-and-delete-operators.md)。|  
|setargv.obj|psetargv.obj|启用命令行参数通配符扩展。  请参见[扩展通配符参数](../c-language/expanding-wildcard-arguments.md)。|  
|smalheap.obj|无|安装一个非常简单的小堆管理器。|  
|threadlocale.obj|pthreadlocale.obj|默认情况下，启用所有新线程的线程区域设置。|  
|wsetargv.obj|pwsetargv.obj|启用命令行参数通配符扩展。  请参见[扩展通配符参数](../c-language/expanding-wildcard-arguments.md)。|  
  
## 请参阅  
 [CRT 库功能](../c-runtime-library/crt-library-features.md)