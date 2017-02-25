---
title: "编译器警告（等级 3）C4635 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4635"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4635"
ms.assetid: b2ba90de-c093-4a76-8076-b65878467574
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器警告（等级 3）C4635
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

XML 文档注释目标: XML 格式不正确: 原因  
  
 编译器发现此 XML 标记存在一些问题。  解决该问题并重新编译  
  
 下面的示例生成 C4635：  
  
```  
// C4635.cpp // compile with: /doc /clr /W3 /c /// <summary> /// The contents of the folder have changed. /// <summary/>   // C4635 // try the following line instead // /// </summary> public ref class Test {};  
```  
  
 请注意，此示例的输出显示：**结束标记“member”与开始标记“summary”不匹配。**  
  
 此示例的问题是 \<summary\> 的结束标记格式不正确，并且编译没有将其识别为 \<summary\> 结束标记。  每个 \/doc 编译中的编译器将 \<member\> 标记嵌入到 .xdc 文件中。  因此，此处问题是结束标记 \<\/member\> 不匹配编译器处理的前一个开始标记 \(\<summary\>\)。