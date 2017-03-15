---
title: "错误 C1308 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1308"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1308"
ms.assetid: 46177997-069e-433a-8e20-93c846d78ffd
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 错误 C1308
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不支持链接程序集  
  
 允许 .netmodule 作为链接器输入，但程序集不能。  当您尝试链接用 `/clr:safe` 编译的程序集时，可能会生成此错误。  
  
 有关更多信息，请参见[作为链接器输入的 .netmodule 文件](../../build/reference/netmodule-files-as-linker-input.md)。  
  
 下面的示例生成 C1308：  
  
```  
// C1308.cpp  
// compile with: /clr:safe /LD  
public ref class MyClass {  
public:  
   int i;  
};  
```  
  
 然后，  
  
```  
// C1308b.cpp  
// compile with: /clr /link C1308b.obj C1308.dll  
// C1308 expected  
#using "C1308.dll"  
int main() {  
   MyClass ^ my = gcnew MyClass();  
}  
```