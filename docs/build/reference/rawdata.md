---
title: "/RAWDATA | Microsoft Docs"
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
  - "/rawdata"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/RAWDATA dumpbin 选项"
  - "原始数据"
  - "RAWDATA dumpbin 选项"
  - "-RAWDATA dumpbin 选项"
ms.assetid: 41cba845-5e1f-415e-9fe4-604a52235983
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /RAWDATA
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/RAWDATA[:{1|2|4|8|NONE[,number]]  
```  
  
## 备注  
 此选项显示文件中每节的原始内容。  参数控制显示格式，如下所示：  
  
|参数|结果|  
|--------|--------|  
|1|默认值。  内容以十六进制字节显示，如果内容具有打印的表示形式，则还显示为 ASCII 字符。|  
|2|内容显示为十六进制的 2 字节值。|  
|4|内容显示为十六进制的 4 字节值。|  
|8|内容显示为十六进制的 8 字节值。|  
|NONE|取消显示原始数据。  此参数对控制 \/ALL 输出很有用。|  
|*数字*|显示的行被设置为每行具有 `number` 个值的宽度。|  
  
 只有 [\/HEADERS](../../build/reference/headers.md) DUMPBIN 选项可用于由 [\/GL](../../build/reference/gl-whole-program-optimization.md) 编译器选项产生的文件。  
  
## 请参阅  
 [DUMPBIN 选项](../../build/reference/dumpbin-options.md)