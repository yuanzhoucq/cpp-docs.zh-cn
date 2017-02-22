---
title: "编译器错误 C2749 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2749"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2749"
ms.assetid: a81aef36-cdca-4d78-89d5-b72eff2500b2
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2749
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”: 使用 \/clr:safe 只能引发或捕获托管类的句柄  
  
 使用 **\/clr:safe** 时，只能引发或捕获引用类型。  
  
 有关详细信息，请参阅[\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
## 示例  
 下面的示例生成 C2749：  
  
```  
// C2749.cpp  
// compile with: /clr:safe  
ref struct MyStruct {  
public:  
   int i;  
};  
  
int main() {  
   MyStruct ^x = gcnew MyStruct;  
  
   // Delete the following 4 lines to resolve.  
   try {   
      throw (1);   // C2749  
   }  
   catch(int){}  
  
   // OK  
   try {  
      throw (x);  
   }  
   catch(MyStruct ^){}   
}  
```