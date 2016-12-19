---
title: "编译器警告（等级 1）C4917 | Microsoft Docs"
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
  - "C4917"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4917"
ms.assetid: c05e2610-4a5d-4f4b-a99b-c15fd7f1d5f1
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4917
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“declarator”: GUID 只能与类、接口或命名空间关联  
  
 [class](../../cpp/class-cpp.md)、[interface](../../cpp/interface.md) 或 [namespace](../../misc/namespace-declaration.md) 之外的用户定义的结构不能有 GUID。  
  
 默认情况下关闭此警告。  有关更多信息，请参见[默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。  
  
 下面的代码示例生成 C4917：  
  
```  
// C4917.cpp  
// compile with: /W1  
#pragma warning(default : 4917)  
__declspec(uuid("00000000-0000-0000-0000-000000000001")) struct S  
{  
} s;   // C4917, don't put uuid on a struct  
  
int main()  
{  
}  
```