---
title: "编译器错误 C2017 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2017"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2017"
ms.assetid: 1083eed9-9906-4a97-883c-54e52d7e82cd
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2017
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

非法的转义序列  
  
 转义序列（如 \\t）出现在字符或字符串常数之外。  
  
 下面的示例生成 C2017：  
  
```  
// C2017.cpp  
int main() {  
   char test1='a'\n;   // C2017  
   char test2='a\n';   // ok  
}  
```  
  
 当 stringize 运算符与包括转义序列的字符串一起使用时会发生 C2017。  
  
 下面的示例生成 C2017：  
  
```  
// C2017b.cpp  
#define TestDfn(x) AfxMessageBox(#x)  
TestDfn(CString("\\") + CString(".h\"\n\n"));   // C2017  
```