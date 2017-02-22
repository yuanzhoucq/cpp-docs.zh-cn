---
title: "PCH 的示例生成文件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "pch"
dev_langs: 
  - "C++"
ms.assetid: daf68983-77dc-45db-8701-aa89ad18910d
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# PCH 的示例生成文件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下列生成文件使用宏和 \!IF、\!ELSE、\!ENDIF 控制流命令结构简化它与项目的适应过程。  
  
```  
# Makefile : Illustrates the effective use of precompiled  
#            headers in a project  
# Usage:     NMAKE option  
# option:    DEBUG=[0|1]  
#            (DEBUG not defined is equivalent to DEBUG=0)  
#  
OBJS = myapp.obj applib.obj  
# List all stable header files in the STABLEHDRS macro.  
STABLEHDRS = stable.h another.h  
# List the final header file to be precompiled here:  
BOUNDRY = stable.h  
# List header files under development here:  
UNSTABLEHDRS = unstable.h  
# List all compiler options common to both debug and final  
# versions of your code here:  
CLFLAGS = /c /W3  
# List all linker options common to both debug and final  
# versions of your code here:  
LINKFLAGS = /NOD /ONERROR:NOEXE  
!IF "$(DEBUG)" == "1"  
CLFLAGS   = /D_DEBUG $(CLFLAGS) /Od /Zi /f  
LINKFLAGS = $(LINKFLAGS) /COD  
LIBS      = slibce  
!ELSE  
CLFLAGS   = $(CLFLAGS) /Oselg /Gs  
LINKFLAGS = $(LINKFLAGS)  
LIBS      = slibce  
!ENDIF  
myapp.exe: $(OBJS)  
    link $(LINKFLAGS) @<<  
$(OBJS), myapp, NUL, $(LIBS), NUL;  
<<  
# Compile myapp  
myapp.obj  : myapp.cpp $(UNSTABLEHDRS)  stable.pch  
    $(CPP) $(CLFLAGS) /Yu$(BOUNDRY)    myapp.cpp  
# Compile applib  
applib.obj : applib.cpp $(UNSTABLEHDRS) stable.pch  
    $(CPP) $(CLFLAGS) /Yu$(BOUNDRY)    applib.cpp  
# Compile headers  
stable.pch : $(STABLEHDRS)  
    $(CPP) $(CLFLAGS) /Yc$(BOUNDRY)    applib.cpp myapp.cpp  
```  
  
 除在[生成过程中的 PCH 文件](../../build/reference/pch-files-in-the-build-process.md)的“使用预编译头文件的生成文件结构”图中显示的 STABLEHDRS、BOUNDRY 和 UNSTABLEHDRS 宏之外，此生成文件还提供 CLFLAGS 宏和 LINKFLAGS 宏。  不论是生成应用程序可执行文件的调试版本还是其最终版本，都必须使用这些宏列出适用的编译器和链接器选项。  还有一个 LIBS 宏，可以用来列出项目所需的库。  
  
 此生成文件还使用 \!IF、\!ELSE、\!ENDIF 检测是否在以下 NMAKE 命令行上定义 DEBUG 符号：  
  
```  
NMAKE DEBUG=[1|0]  
```  
  
 此功能使您可以在开发期间和程序的最终版本中使用相同的生成文件。对于最终版本，使用 DEBUG\=0。  下列命令行是等效的：  
  
```  
NMAKE   
NMAKE DEBUG=0  
```  
  
 有关生成文件的更多信息，请参见 [NMAKE 参考](../../build/nmake-reference.md)。  另请参见[编译器选项](../../build/reference/compiler-options.md)和[链接器选项](../../build/reference/linker-options.md)。  
  
## 请参阅  
 [在项目中使用预编译头](../../build/reference/using-precompiled-headers-in-a-project.md)