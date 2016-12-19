---
title: "编译器警告（等级 4）C4001 | Microsoft Docs"
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
  - "C4001"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4001"
ms.assetid: 414a47fe-d597-425e-9374-6a569231dc0a
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4001
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用了非标准扩展“single line comment”  
  
 单行注释在 C\+\+ 中是标准格式，而在 C 中不是标准格式。  在严格的 ANSI 兼容性 \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 下，包含单行注释的 C 文件因使用非标准扩展而生成 C4001。  因为单行注释是 C\+\+ 中的标准格式，所以在用 Microsoft 扩展 \(\/Ze\) 编译时，包含单行注释的 C 文件不产生 C4001。  
  
## 示例  
 若要禁用警告，请取消注释 [\#pragma warning\(disable:4001\)](../../preprocessor/warning.md)。  
  
```  
// C4001.cpp  
// compile with: /W4 /Za /TC  
// #pragma warning(disable:4001)  
int main()  
{  
   // single-line comment in main  
   // C4001  
}  
```