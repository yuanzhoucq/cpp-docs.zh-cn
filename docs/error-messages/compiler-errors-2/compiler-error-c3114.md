---
title: "编译器错误 C3114 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3114"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3114"
ms.assetid: b5d2df4f-87d0-4292-9981-25c6a6013c05
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C3114
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“argument”: 不是有效的命名特性参数  
  
 为使特性类数据成员为有效的命名参数，一定不能将其标记为 `static`、`const` 或 `literal`。  如果是一个属性，则该属性一定不能是 `static`，并且必须有 get 和 set 访问器。  
  
 有关更多信息，请参见[属性](../../windows/property-cpp-component-extensions.md)和[用户定义的特性](../../windows/user-defined-attributes-cpp-component-extensions.md)。  
  
## 示例  
 下面的示例生成 C3114。  
  
```  
// C3114.cpp  
// compile with: /clr /c  
public ref class A : System::Attribute {  
public:  
   static property int StaticProp {  
      int get();  
   }  
  
   property int Prop2 {  
      int get();  
      void set(int i);  
   }  
};  
  
[A(StaticProp=123)]   // C3114  
public ref class R {};  
  
[A(Prop2=123)]   // OK  
public ref class S {};  
```