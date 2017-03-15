---
title: "/RANGE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/RANGE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/RANGE dumpbin 选项"
  - "-RANGE dumpbin 选项"
ms.assetid: 7eeba266-32be-49cc-a350-96bdf541f98a
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /RANGE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

修改与其他 dumpbin 选项（如 \/RAWDATA 或 \/DISASM）一起使用时 dumpbin 的输出。  
  
## 语法  
  
```  
/RANGE:vaMin[,vaMax]  
```  
  
## Flags  
 **vaMin**  
 dumpbin 操作的起始位置的虚拟地址。  
  
 **vaMax**（可选）  
 dumpbin 操作的结束位置的虚拟地址。  如果不指定，则 dumpbin 将进行到文件的末尾。  
  
## 备注  
 若要查看映像的虚拟地址，请使用映像的映射文件 \(RVA \+ Base\)、dumpbin 的 **\/DISASM** 或 **\/HEADERS** 选项或者 Visual Studio 调试器中的反汇编窗口。  
  
## 示例  
 在本示例中，**\/range** 用于修改 **\/disasm** 选项的显示。  在本示例中，起始值表示为十进制数，而结束值指定为十六进制数。  
  
```  
dumpbin /disasm /range:4219334,0x004061CD t.exe  
```  
  
## 请参阅  
 [DUMPBIN 选项](../../build/reference/dumpbin-options.md)