---
title: "编译器错误 C3917 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3917"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3917"
ms.assetid: a24cd0c9-262f-46e5-9488-1c01f945933d
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 编译器错误 C3917
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“property”: 过时的构造声明样式  
  
 属性或事件定义使用了早期版本中的语法。  
  
 如果要使用早期版本中的语法，请使用 [\/clr:oldSyntax](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
 有关更多信息，请参见[属性](../../windows/property-cpp-component-extensions.md)。  
  
## 示例  
  
```  
// C3917.cpp  
// compile with: /clr /c  
public ref class  C {  
private:  
   int m_length;  
public:  
   C() {  
      m_length = 0;  
   }  
  
   property int get_Length();   // C3917  
  
   // The correct property definition:  
   property int Length {  
      int get() {  
         return m_length;  
      }  
  
      void set( int i ) {  
         m_length = i;  
      }  
   }  
};  
```