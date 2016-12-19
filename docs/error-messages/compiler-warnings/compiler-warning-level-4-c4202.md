---
title: "编译器警告（等级 4）C4202 | Microsoft Docs"
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
  - "C4202"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4202"
ms.assetid: 253293aa-97a3-4878-a2e8-c6cc9e20b1cb
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4202
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用了非标准扩展:“...”: 名称列表中的原型参数非法  
  
 旧式函数定义包含变量参数。  这些定义在 ANSI 兼容性 \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 下生成错误。  
  
## 示例  
  
```  
// C4202.c  
// compile with: /W4  
void func( a, b, ...)   // C4202  
int a, b;  
{}  
  
int main()  
{  
}  
```