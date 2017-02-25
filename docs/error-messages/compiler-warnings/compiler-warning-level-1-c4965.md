---
title: "编译器警告（等级 1）C4965 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4965"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4965"
ms.assetid: 47f3f6dc-459b-4a25-9947-f394c8966cb5
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# 编译器警告（等级 1）C4965
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

整数 0 的隐式装箱；请使用 nullptr 或显式强制转换  
  
 Visual C\+\+ 具有值类型的隐式装箱。  使用 C\+\+ 托管扩展导致空赋值的指令现在变为对装箱的 int 赋值。  
  
 有关详细信息，请参阅[装箱](../../windows/boxing-cpp-component-extensions.md)。  
  
## 示例  
 下面的示例生成 C4965。  
  
```  
// C4965.cpp  
// compile with: /clr /W1  
int main() {  
   System::Object ^o = 0;   // C4965  
  
   // the previous line is the same as the following line  
   // using Managed Extensions for C++  
   // System::Object *o = __box(0);  
  
   // OK  
   System::Object ^o2 = nullptr;  
   System::Object ^o3 = safe_cast<System::Object^>(0);  
}  
```