---
title: "编译器警告（等级 2 和等级 4）C4200 | Microsoft Docs"
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
  - "C4200"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4200"
ms.assetid: e44d6073-937f-42b7-acc1-65e802b475c6
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 2 和等级 4）C4200
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用了非标准扩展：结构\/联合中大小为零的数组  
  
 指示结构或联合包含大小为零的数组。  
  
 大小为零数组的声明为 Microsoft 扩展。  编译 C\+\+ 文件时，这会造成等级 2 警告，而在编译 c 文件时会造成等级 4 警告。  C\+\+ 编译也发出以下警告：“当 UDT 包含大小为零的数组时，无法生成复制构造函数或副本赋值运算符。”此示例生成警告 C4200：  
  
```cpp  
// C4200.cpp  
// compile by using: cl /W4 c4200.cpp  
struct A {  
    int a[0];  // C4200  
};  
int main() {  
}  
```  
  
 此非标准扩展常用于将代码与具有可变长度的外部数据结构连接起来。  如果此方案适用于你的代码，则可禁用此警告：  
  
## 示例  
  
```cpp  
// C4200b.cpp  
// compile by using: cl /W4 c4200a.cpp  
#pragma warning(disable : 4200)  
struct A {  
    int a[0];  
};  
int main() {  
}  
```