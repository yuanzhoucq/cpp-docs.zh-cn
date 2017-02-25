---
title: "链接器工具错误 LNK2022 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2022"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2022"
ms.assetid: d2128c73-dde3-4b8e-a9b2-0a153acefb3b
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# 链接器工具错误 LNK2022
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

元数据操作失败 \(HRESULT\) : error\_message  
  
 链接器在合并元数据时检测到错误。  必须解决元数据错误，链接才能成功。  
  
 诊断此问题的一种方式是在对象文件上运行 **ildasm –tokens**，以找出哪些类型的标记在 `error_message` 中列出了，并查找不同之处。在元数据中，即使只有 LayoutType 特性不同，同名的两个不同类型也是无效的。  
  
 导致 LNK2022 的一个原因是当一个类型（例如结构）位于多个同名 compiland 中，但定义冲突，并且您用 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 进行编译时。在此情况下，请确保该类型在所有 compiland 中具有相同的定义。该类型名称在 `error_message` 中列出。  
  
 导致 LNK2022 的另一个可能的原因是当链接器在为编译器（使用 [\#using](../../preprocessor/hash-using-directive-cpp.md)）所指定位置之外的地方找到源数据文件时。  确保元文件 \(.dll ornetmodule）在传递给链接器时位于与传递给编译器时相同的位置。  
  
 生成 ATL 应用程序时，如果至少在一个 compiland 中使用了 [\_ATL\_MIXED](../Topic/_ATL_MIXED.md)，则需要在所有 compiland 中使用。  
  
## 示例  
 下面的示例定义了一个空类型。  
  
```  
// LNK2022_a.cpp  
// compile with: /clr /c  
public ref class Test {};  
```  
  
## 示例  
 此示例演示，不能将两个包含相同名称但定义不同的类型的源代码文件进行链接。  
  
 下面的示例生成 LNK2022。  
  
```  
// LNK2022_b.cpp  
// compile with: LNK2022_a.cpp /clr /LD   
// LNK2022 expected  
public ref class Test {  
   void func() {}  
   int var;  
};  
```