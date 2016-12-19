---
title: "编译器错误 C3159 | Microsoft Docs"
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
  - "C3159"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3159"
ms.assetid: e115cc76-0021-4568-95fd-61a324c41a85
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3159
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“pointer”: 不能声明指向值类型的指针数组  
  
 不能声明指向值类型的指针数组。  
  
 只有使用 **\/clr:oldSyntax** 时才可能出现 C3159 错误。  
  
 下面的示例生成 C3159：  
  
```  
// C3159.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__value struct B {  
};  
  
void f( B*[] );   // C3159  
  
int main() {  
}  
```