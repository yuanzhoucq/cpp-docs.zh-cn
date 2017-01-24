---
title: "为自己的类重载 &gt;&gt; 运算符 | Microsoft Docs"
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
  - "运算符 >>, 针对您自己的类进行重载"
  - "operator>>"
  - "operator>>, 针对您自己的类进行重载"
ms.assetid: 40dab4e0-3f97-4745-9cc8-b86e740fa246
caps.latest.revision: 8
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 为自己的类重载 &gt;&gt; 运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

输入流针对标准类型使用提取 \(`>>`\) 运算符。  您可以编写的类似运算符提取自己的类型；成功取决于精确使用空白。  
  
 这是从早期运算符的示例显示的 `Date` 的类：  
  
```  
istream& operator>> ( istream& is, Date& dt )  
{  
   is >> dt.mo >> dt.da >> dt.yr;  
   return is;  
}  
```  
  
## 请参阅  
 [输入流](../standard-library/input-streams.md)