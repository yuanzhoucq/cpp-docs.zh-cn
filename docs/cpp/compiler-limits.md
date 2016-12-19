---
title: "编译器限制 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe 编译器, 对语言构造的限制"
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 编译器限制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ 标准建议对各种语言构造施加限制。  下面是 Visual C\+\+ 编译器不会在其中实施建议的限制的情况的列表。  第一个数字是 ISO C\+\+ 11 标准（INCITS\/ISO\/IEC 14882\-2011\[2012\]，附件 B）中建立的限制，而第二个数字是由 Visual C\+\+ 实现的限制：  
  
-   复合语句、迭代控制结构和选择控制结构的嵌套级别 \[C\+\+ 标准：256\]（Visual C\+\+ 编译器：具体取决于嵌套语句的组合，但通常介于 100 和 110 之间）。  
  
-   一个宏定义中的参数 \[C\+\+ 标准：256\]（Visual C\+\+ 编译器：127）。  
  
-   一个宏调用中的参数 \[C\+\+ 标准：256\]（Visual C\+\+ 编译器：127）。  
  
-   字符串文本或宽字符串文本中的字符（串联后）\[C\+\+ 标准：65536\]（Visual C\+\+ 编译器：包括 `null` 终止符的 65535 个单字节字符，以及包括 `null` 终止符的 32767 个双字节字符）。  
  
-   单个 `struct-declaration-list` 中的嵌套类、结构或联合定义的级别 \[C\+\+ 标准：256\]（Visual C\+\+ 编译器：16）。  
  
-   构造函数定义中的成员初始值设定项 \[C\+\+ 标准：6144\]（Visual C\+\+ 编译器：至少为 6144）。  
  
-   一个标识符的范围限定 \[C\+\+ 标准：256\]（Visual C\+\+ 编译器：127）。  
  
-   嵌套 `extern` 规范 \[C\+\+ 标准：1024\]（Visual C\+\+ 编译器：9（未计算全局范围中的隐式 `extern` 规范；如果计算全局范围中的隐式 `extern` 规范，则为 10。）。  
  
-   模板声明中的模板参数 \[C\+\+ 标准：1024\]（Visual C\+\+ 编译器：2046）。  
  
## 请参阅  
 [非标准行为](../cpp/nonstandard-behavior.md)