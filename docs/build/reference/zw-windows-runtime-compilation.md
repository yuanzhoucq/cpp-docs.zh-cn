---
title: "/ZW（Windows 运行时编译） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.CompileAsWinRT"
  - "/zw"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ZW"
  - "/ZW 编译器选项"
  - "Windows 运行时编译器选项"
  - "-ZW"
  - "-ZW 编译器选项"
ms.assetid: 0fe362b0-9526-498b-96e0-00d7a965a248
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# /ZW（Windows 运行时编译）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

编译源代码以支持适用于创建 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用的 [!INCLUDE[cppwrt](../../build/reference/includes/cppwrt_md.md)] \([!INCLUDE[cppwrt_short](../../build/reference/includes/cppwrt_short_md.md)]\)。  
  
 在使用 **\/ZW** 进行编译时，还应始终指定 **\/EHsc**。  
  
## 语法  
  
```cpp  
/ZW /EHsc /ZW:nostdlib /EHsc  
```  
  
## 参数  
 nostdlib  
 指示 Platform.winmd、Windows.Foundation.winmd 以及其他默认 Windows 元数据 \(.winmd\) 文件未自动包含在该编译中。  相反，你必须使用 [\/FU（命名强制 \#using 文件）](../../build/reference/fu-name-forced-hash-using-file.md)编译器选项显式指定 Windows 元数据文件。  
  
## 备注  
 在指定 **\/ZW** 选项时，编译器将支持以下功能：  
  
-   你的应用需要在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中执行的所需元数据文件、命名空间、数据类型以及函数。  
  
-   自动引用计数 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 对象，并在对象的引用计数归零时自动丢弃该对象。  
  
 由于增量链接器不支持通过使用 **\/ZW** 选项将 Windows 元数据包含在 .obj 文件中，因此 [\/Gm（启用最小重新生成）](../../build/reference/gm-enable-minimal-rebuild.md) 选项与 **\/ZW** 不兼容。  
  
 有关详细信息，请参阅[Visual C\+\+ 语言参考](../Topic/Visual%20C++%20Language%20Reference%20\(C++-CX\).md)。  
  
## 要求  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)