---
title: "编译器错误 C3891 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3891"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3891"
ms.assetid: 6e1a9458-97f5-4580-bc0f-aa97a1bfd20d
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C3891
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“var”: literal 数据成员不能用作左值  
  
 [literal](../../windows/literal-cpp-component-extensions.md) 变量是常数，在声明中对它初始化后其值不可更改。  
  
 下面的示例生成 C3891：  
  
```  
// C3891.cpp  
// compile with: /clr  
ref struct Y1 {  
   literal int staticConst = 9;  
};  
  
int main() {  
   Y1::staticConst = 0;   // C3891  
}  
```