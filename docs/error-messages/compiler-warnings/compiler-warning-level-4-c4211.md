---
title: "编译器警告（等级 4）C4211 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4211"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4211"
ms.assetid: 3eea3455-6faa-4cdb-8730-73db7026bd1f
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 4）C4211
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用了非标准扩展 : 将“extern”重新定义为“static”  
  
 在默认 Microsoft 扩展 \(\/Ze\) 下，可以将 `extern` 标识符重定义为 **static**。  
  
## 示例  
  
```  
// C4211.c  
// compile with: /W4  
extern int i;  
static int i;   // C4211  
  
int main()  
{  
}  
```  
  
 这种重定义在 ANSI 兼容性 \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 下无效。  
  
## 请参阅  
 [\(NOTINBUILD\)Static Storage\-Class Specifiers](http://msdn.microsoft.com/zh-cn/3ba9289a-a412-4a17-b319-ceb2c087df48)