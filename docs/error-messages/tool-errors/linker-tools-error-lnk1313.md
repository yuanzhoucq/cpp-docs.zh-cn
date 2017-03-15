---
title: "链接器工具错误 LNK1313 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1313"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1313"
ms.assetid: 5df0b72e-bb3f-428c-8d84-6084238f9827
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 链接器工具错误 LNK1313
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检测到 ijw\/native 模块；不能与纯模块链接  
  
 Visual C\+\+ 的当前版本不支持将本机或混合托管\/本机.obj 文件与用 **\/clr:pure** 编译的 .obj 文件进行链接。  
  
## 示例  
  
```  
// LNK1313.cpp  
// compile with: /c /clr:pure  
// a pure module  
int main() {}  
```  
  
## 示例  
  
```  
// LNK1313_b.cpp  
// compile with: /c /clr  
// an IJW module  
void test(){}  
```  
  
## 示例  
 下面的示例将生成 LNK1313。  
  
```  
// LNK1313_c.cpp  
// compile with: /link LNK1313.obj LNK1313_b.obj  
// LNK1313 warning expected  
```