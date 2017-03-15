---
title: "编译器警告（等级 1）C4407 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4407"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4407"
ms.assetid: 32bc2c21-363a-4bb8-b486-725faeaededc
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 编译器警告（等级 1）C4407
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在指向成员表示形式的不同指针之间进行转换，编译器可能生成不正确的代码  
  
 检测到不正确的转换。  
  
 C4407 可能是由于在 Visual C\+\+ 2005 中所完成的编译器一致性工作而产生的。  指向成员的指针现在需要限定名称和 address\-of 运算符\(&\)。  
  
 如果在多重继承的指向成员的指针与单个继承的指向成员的指针之间进行强制转换，则可能发生 C4407。  此操作有时可以进行，有时不能进行，因为单个继承的指向成员的指针表示拥有的信息不足。  使用 **\/vmm** 进行编译可能会有帮助（有关更多信息，请参见 [\/vmm、\/vms、\/vmv（通用表示形式）](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)）。  也可以尝试重新安排基类；编译器检测转换中的信息丢失，因为基类距派生类的偏移量不为零。  
  
 下面的示例生成 C4407：  
  
```  
// C4407.cpp  
// compile with: /W1 /c  
struct C1 {};  
struct C2 {};  
struct C3 : C1, C2 {};  
  
typedef void(C3::*PMF_C3)();  
typedef void(C2::*PMF_C2)();  
  
PMF_C2 f1(PMF_C3 pmf) {  
   return (PMF_C2)pmf;   // C4407, change type of cast,  
   // or reverse base class inheritance of C3 (i.e. : C2, C1)  
}  
```