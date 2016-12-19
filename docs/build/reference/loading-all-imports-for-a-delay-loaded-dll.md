---
title: "加载被延迟加载的 DLL 的所有导入 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__HrLoadAllImportsForDll 链接器选项"
ms.assetid: 975fcd97-1a56-4a16-9698-e1a249d2d592
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 加载被延迟加载的 DLL 的所有导入
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

delayhlp.cpp 中定义的 **\_\_HrLoadAllImportsForDll** 函数通知链接器加载用 [\/delayload](../../build/reference/delayload-delay-load-import.md) 链接器选项指定的 DLL 中的所有导入。  
  
 加载所有导入使您能够将错误处理置于代码中的一个地方，而无需在对导入的实际调用周围使用异常处理。  它还避免了因 Helper 代码加载导入失败而导致应用程序的一部分在进程中失败。  
  
 调用 **\_\_HrLoadAllImportsForDll** 不会更改挂钩和错误处理的行为；有关更多信息，请参见[错误处理和通知](../../build/reference/error-handling-and-notification.md)。  
  
 通过 **\_\_HrLoadAllImportsForDll** 的 DLL 名称与 DLL 自身内存储的名称进行比较，区分大小写。  
  
 下面的示例显示如何调用 **\_\_HrLoadAllImportsForDll**：  
  
```  
if (FAILED(__HrLoadAllImportsForDll("delay1.dll"))) {  
   printf ( "failed on snap load, exiting\n" );  
   exit(2);  
}  
```  
  
## 请参阅  
 [链接器的延迟加载 DLL 支持](../../build/reference/linker-support-for-delay-loaded-dlls.md)