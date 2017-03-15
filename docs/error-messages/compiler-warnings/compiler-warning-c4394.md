---
title: "编译器警告 C4394 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4394"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4394"
ms.assetid: 5de94de0-17e3-4e7c-92f4-5c3c1b825120
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 编译器警告 C4394
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: per\-appdomain 符号不应该用 \_\_declspec\(dllexport\) 进行标记  
  
 用 [appdomain](../../cpp/appdomain.md) `__declspec` 修饰符标记的函数编译到 MSIL（而非本机），托管函数不支持导出表（[export](../../windows/export.md) `__declspec` 修饰符）。  
  
 可以声明托管函数具有公共可访问性。  关更多信息，请参见[类型可见性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) 和 [成员可见性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility) 。  
  
 C4394 始终按错误发出。可以使用 `#pragma warning` 或 **\/wd** 关闭此警告；有关更多信息，请参见 [警告](../../preprocessor/warning.md) 或 [\/w、\/Wn、\/WX、\/Wall、\/wln、\/wdn、\/wen、\/won（警告等级）](../../build/reference/compiler-option-warning-level.md)。  
  
## 示例  
 下面的示例生成 C4394。  
  
```  
// C4394.cpp  
// compile with: /clr /c  
__declspec(dllexport) __declspec(appdomain) int g1 = 0;   // C4394  
__declspec(dllexport) int g2 = 0;   // OK  
```