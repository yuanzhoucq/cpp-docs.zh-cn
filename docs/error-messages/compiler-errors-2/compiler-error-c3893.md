---
title: "编译器错误 C3893 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3893"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3893"
ms.assetid: 90d52eae-6ef2-4db1-b7ad-92f9e8b140fb
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 编译器错误 C3893
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“var”: initonly 数据成员的左值只允许在类“type\_name”的实例构造函数中使用  
  
 静态 [initonly](../../dotnet/initonly-cpp-cli.md) 数据成员只能使它们的地址在静态构造函数中采用。  
  
 实例（非静态）initonly 数据成员只能使它们的地址在实例（非静态）构造函数中采用。  
  
 下面的示例生成 C3893：  
  
```  
// C3893.cpp  
// compile with: /clr  
ref struct Y1 {  
   Y1() : data_var(0) {  
      int% i = data_var;   // OK  
   }  
   initonly int data_var;  
};  
  
int main(){  
   Y1^ y= gcnew Y1;  
   int% i = y->data_var;   // C3893  
}  
```