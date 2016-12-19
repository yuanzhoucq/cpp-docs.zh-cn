---
title: "链接器工具错误 LNK1237 | Microsoft Docs"
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
  - "LNK1237"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1237"
ms.assetid: 8722ffa8-096a-4bb0-85f9-f3aa0e10872a
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具错误 LNK1237
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在代码生成过程中，编译器引入了使用 \/GL 编译的模块“module”中定义的符号“symbol”的引用  
  
 代码生成期间，如果引入的符号稍后将解析为使用 **\/GL** 编译的定义，则编译器不应引入这些符号。  `symbol` 是一种符号，它在引入后将被解析为使用 **\/GL** 编译的定义。  
  
 有关详细信息，请参阅[\/GL（全程序优化）](../../build/reference/gl-whole-program-optimization.md)。  
  
 要解决 LNK1237，请不要使用 **\/GL** 编译符号或使用 [\/INCLUDE（强制符号引用）](../../build/reference/include-force-symbol-references.md) 强制引用符号。  
  
## 示例  
 下面的示例生成 LNK1237。  若要解决此问题，请不要在 LNK1237\_a.cpp 中初始化该数组以及将 **\/include:\_\_chkstk** 添加到链接命令中。  
  
```  
// LNK1237_a.cpp  
int main() {  
   char c[5000] = {0};  
}  
```  
  
```  
// LNK1237_b.cpp  
// compile with: /GS- /GL /c LNK1237_a.cpp  
// processor: x86  
// post-build command: (lib LNK1237_b.obj /LTCG & link LNK1237_a.obj LNK1237_b.lib /nodefaultlib /entry:main /LTCG)  
extern "C" void _chkstk(size_t s) {}  
```