---
title: "编译器错误 C3828 | Microsoft Docs"
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
  - "C3828"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3828"
ms.assetid: 8d9cee75-9504-4bc8-88b6-2413618a3f45
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3828
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“object type”：在创建托管或 WinRT 类的实例时不允许使用位置参数  
  
 创建托管类型或 Windows 运行时类型的对象时，不能使用运算符 [gcnew](../../windows/ref-new-gcnew-cpp-component-extensions.md) 或 [new](../../cpp/new-operator-cpp.md) 的放置形式。  
  
 下列示例生成 C3828 并演示如何修复此错误：  
  
```  
// C3828a.cpp  
// compile with: /clr  
ref struct M {  
};  
  
ref struct N {  
   static array<char>^ bytes = gcnew array<char>(256);  
};  
  
int main() {  
   M ^m1 = new (&N::bytes) M();   // C3828  
   // The following line fixes the error.  
   // M ^m1 = gcnew M();  
}  
```