---
title: "编译器警告（等级 1）C4218 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4218"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4218"
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4218
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用了非标准扩展 : 必须至少指定一个存储类或一个类型  
  
 在默认 Microsoft 扩展 \(\/Ze\) 下，可以在不指定类型或存储类的情况下声明变量。  默认类型为 `int`。  
  
## 示例  
  
```  
// C4218.c  
// compile with: /W4  
i;  // C4218  
  
int main()  
{  
}  
```  
  
 这样的声明在 ANSI 兼容性 \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 下无效。