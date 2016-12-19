---
title: "预定义的规则 | Microsoft Docs"
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
  - "规则, 预定义的"
  - "NMAKE 程序, 预定义的规则"
  - "NMAKE 中的预定义规则"
ms.assetid: 638cdc3f-4aba-4b4f-96e3-ad65b0364f12
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 预定义的规则
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

预定义的推理规则使用 NMAKE 提供的命令和选项宏。  
  
|规则|命令|默认<br /><br /> 操作|批处理<br /><br /> 规则|nmake 运行的平台|  
|--------|--------|---------------|----------------|-----------------|  
|.asm.exe|$\(AS\) $\(AFLAGS\) $\<（用${AS}汇编器传${ASFLAGS}汇编参数的汇编指令）|ml $\<（汇编语言）|no|x86|  
|.asm.obj|$\(AS\) $\(AFLAGS\) \/c $\<（用${AS}汇编器传${ASFLAGS}汇编参数的汇编指令）|ml \/c $\<（汇编语言）|yes|x86|  
|.asm.exe|$\(AS\) $\(AFLAGS\) $\<（用${AS}汇编器传${ASFLAGS}汇编参数的汇编指令）|ml64 $\<（汇编语言）|no|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|.asm.obj|$\(AS\) $\(AFLAGS\) \/c $\<（用${AS}汇编器传${ASFLAGS}汇编参数的汇编指令）|ml64 \/c $\<（汇编语言）|yes|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|.c.exe|$\(CC\) $\(CFLAGS\) $\<（用${CC}汇编器传${CFLAGS}汇编参数的汇编指令）|cl $\<（汇编语言）|no|所有|  
|.c.obj|$\(CC\) $\(CFLAGS\) \/c $\<（用${CC}汇编器传${CFLAGS}汇编参数的汇编指令）|cl \/c $\<（汇编语言）|yes|所有|  
|.cc.exe|$\(CC\) $\(CFLAGS\) $\<（用${CC}汇编器传${CFLAGS}汇编参数的汇编指令）|cl $\<（汇编语言）|no|所有|  
|.cc.obj|$\(CC\) $\(CFLAGS\) \/c $\<（用${CC}汇编器传${CFLAGS}汇编参数的汇编指令）|cl \/c $\<（汇编语言）|yes|所有|  
|.cpp.exe|$\(CPP\) $\(CPPFLAGS\) $\<（用${CPP}汇编器传${CPPFLAGS}汇编参数的汇编指令）|cl $\<（汇编语言）|no|所有|  
|.cpp.obj|$\(CPP\) $\(CPPFLAGS\) \/c $\<（用${CPP}汇编器传${CPPFLAGS}汇编参数的汇编指令）|cl \/c $\<（汇编语言）|yes|所有|  
|.cxx.exe|$\(CXX\) $\(CXXFLAGS\) $\<（用${CXX}汇编器传${CXXFLAGS}汇编参数的汇编指令）|cl $\<（汇编语言）|no|所有|  
|.cxx.obj|$\(CXX\) $\(CXXFLAGS\) \/c $\<（用${CXX}汇编器传${CXXFLAGS}汇编参数的汇编指令）|cl \/c $\<（汇编语言）|yes|所有|  
|.rc.res|$\(RC\) $\(RFLAGS\) \/r $\<（汇编语言）|rc \/r $\<（汇编语言）|no|所有|  
  
## 请参阅  
 [推理规则](../build/inference-rules.md)