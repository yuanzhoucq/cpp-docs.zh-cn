---
title: "/SECTION (EDITBIN) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/section"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/SECTION editbin 选项"
  - "节中的对齐字符"
  - "SECTION editbin 选项"
  - "-SECTION editbin 选项"
ms.assetid: 4680ab4e-c984-4251-8241-93440cad7615
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /SECTION (EDITBIN)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/SECTION:name[=newname][,attributes][alignment]  
```  
  
## 备注  
 此选项更改节的特性，重写当初编译或链接该节的对象文件时设置的特性。  
  
 在冒号 \( **:** \) 后指定节的 *name*。  若要更改节名，在 *name* 后加上等号 \(\=\) 和节的 *newname*。  
  
 若要设置或更改节的 `attributes`，请指定一个逗号 \(**,**\)，在它后面跟一个或多个特性字符。  若要取反特性，请在特性字符前使用一个感叹号 \(\!\)。  下列字符指定内存特性：  
  
|特性|设置|  
|--------|--------|  
|c|代码|  
|d|可丢弃的|  
|e|executable|  
|i|初始化数据|  
|k|缓存虚拟内存|  
|m|链接移除|  
|o|链接信息|  
|p|分页虚拟内存|  
|r|read|  
|s|共享|  
|u|未初始化数据|  
|w|write|  
  
 若要控制 *alignment*，请指定字符 **A**，后跟用于设置对齐大小（以字节计）的下列字符之一，如下所示：  
  
|字符|对齐大小（以字节计）|  
|--------|----------------|  
|1|1|  
|2|2|  
|4|4|  
|8|8|  
|p|16|  
|t|32|  
|s|64|  
|x|不对齐|  
  
 指定 `attributes` 和 *alignment* 字符为不含空白的字符串。  字符不区分大小写。  
  
## 请参阅  
 [EDITBIN 选项](../../build/reference/editbin-options.md)