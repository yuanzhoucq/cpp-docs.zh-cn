---
title: "链接器工具警告 LNK4247 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4247"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4247"
ms.assetid: 085d7fdf-9eaf-4641-8473-6eaadd073c7b
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 链接器工具警告 LNK4247
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

入口点“decorated\_function\_name”已有线程特性；“attribute”被忽略  
  
 用 [\/ENTRY（入口点符号）](../../build/reference/entry-entry-point-symbol.md) 指定的入口点已有线程特性，但是又用一个不同的线程模型指定了 [\/CLRTHREADATTRIBUTE（设置 CLR 线程特性）](../../build/reference/clrthreadattribute-set-clr-thread-attribute.md)。  
  
 链接器忽略用 \/CLRTHREADATTRIBUTE 指定的值。  
  
 解决此警告的方法是：  
  
-   从生成中移除 \/CLRTHREADATTRIBUTE。  
  
-   从源代码文件中移除特性。  
  
-   从源代码中移除特性并从生成中移除 \/CLRTHREADATTRIBUTE，然后接受默认的 CLR 线程模型。  
  
-   更改传递给 \/CLRTHREADATTRIBUTE 的值，使它与源代码中的特性一致。  
  
-   更改源代码中的特性，使它与传递给 \/CLRTHREADATTRIBUTE 的值一致。  
  
 下面的示例生成 LNK4247  
  
```  
// LNK4247.cpp  
// compile with: /clr /c  
// post-build command: link /CLRTHREADATTRIBUTE:STA LNK4247.obj /entry:functionTitle /SUBSYSTEM:Console  
 [System::MTAThreadAttribute]  
void functionTitle (){}  
```