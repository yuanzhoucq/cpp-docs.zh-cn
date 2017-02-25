---
title: "编译器警告（等级 1）C4691 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4691"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4691"
ms.assetid: 722133d9-87f6-46c1-9e86-9825453d6999
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 编译器警告（等级 1）C4691
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”: 引用的类型应在未引用的程序集“file”中，却使用了当前翻译单元中定义的类型  
  
 未引用包含原始类型定义的元数据文件，并且编译器使用的是局部类型定义。  
  
 在重新生成 *file* 的情况下，可用杂注 [警告](../../preprocessor/warning.md) 忽略或关闭 C4691。也就是说，如果正在生成的文件与编译器期望在其中找到类型定义的文件相同，可以忽略 C4691。  
  
 但是，如果编译器使用的定义不是来自在元数据中引用的同一程序集，可能发生意外的行为；CLR 类型不仅由类型名称决定，也由程序集决定。也就是说，来自程序集 z.dll 的类型 Z 不同于来自程序集 y.dll 的类型 Z。  
  
## 示例  
 此示例包含原始类型定义。  
  
```  
// C4691_a.cpp  
// compile with: /clr /LD /W1  
public ref class Original_Type {};  
```  
  
## 示例  
 此示例引用 C4691\_a.dll 并声明一个类型为 Original\_Type 的字段。  
  
```  
// C4691_b.cpp  
// compile with: /clr /LD  
#using "C4691_a.dll"  
public ref class Client {  
public:  
   Original_Type^ ot;  
};  
```  
  
## 示例  
 下面的示例生成 C4691。注意：此示例包含 Original\_Type 的定义并且不引用 C4691a.dll。  
  
 若要消除此警告，请引用包含原始类型定义的元数据文件并移除局部声明和定义。  
  
```  
// C4691_c.cpp  
// compile with: /clr /LD /W1  
// C4691 expected  
  
// Uncomment the following line to resolve.  
// #using "C4691_a.dll"  
#using "C4691_b.dll"  
  
// Delete the following line to resolve.  
ref class Original_Type;  
  
public ref class MyClass : Client {};  
```