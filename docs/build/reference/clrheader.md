---
title: "/CLRHEADER | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/CLRHEADER"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/CLRHEADER dumpbin 选项"
  - "CLRHEADER dumpbin 选项"
  - "-CLRHEADER dumpbin 选项"
ms.assetid: cf73424f-4541-47e2-b94e-69b95266ef2a
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# /CLRHEADER
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/CLRHEADER file  
```  
  
## 备注  
 其中：  
  
 `file`  
 用 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 生成的图像文件。  
  
## 备注  
 CLRHEADER 显示有关在任何托管程序中使用的 .NET 头的信息。  输出显示 .NET 头及其中各节的位置和大小（以字节计）。  
  
 只有 [\/HEADERS](../../build/reference/headers.md) DUMPBIN 选项可用于由 [\/GL](../../build/reference/gl-whole-program-optimization.md) 编译器选项产生的文件。  
  
 当对使用 \/clr 编译的文件使用 \/CLRHEADER 时，在 Dumpbin 输出中将出现 **clr Header:** 节。**flags** 的值指示所使用的 \/clr 选项：  
  
-   0 \-\- \/clr（映像可能包含本机代码）。  
  
-   1 \-\- \/clr:safe（映像只是 MSIL 映像，可在任何 CLR 平台上运行，而且可能可以验证）。  
  
-   3 \-\- \/clr:pure（映像只是 MSIL 映像，但只能在 x86 平台上运行）。  
  
 还可以通过编程方式检查是否为公共语言运行时生成了映像。有关详细信息，请参阅[如何：确定映像为本机映像还是 CLR 映像](../../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)。  
  
## 请参阅  
 [DUMPBIN 选项](../../build/reference/dumpbin-options.md)