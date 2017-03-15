---
title: "C++ 中的声明点 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "声明点"
ms.assetid: 92ea8707-80cb-497c-b479-f907b8401859
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++ 中的声明点
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

名称被视为在紧靠其声明符之后，但位于其（可选）初始值设定项之前的位置进行声明。  （有关声明符的详细信息，请参阅[声明符](http://msdn.microsoft.com/zh-cn/8a7b9b51-92bd-4ac0-b3fe-0c4abe771838)。）  
  
 请看以下示例：  
  
```  
// point_of_declaration1.cpp  
// compile with: /W1   
double dVar = 7.0;  
int main()  
{  
   double dVar = dVar;   // C4700  
}  
```  
  
 如果声明的位置位于初始化之后，则本地 `dVar` 将初始化为 7.0（全局变量 `dVar` 的值）。  但是，由于情况并非如此，`dVar` 将初始化为未定义值。  
  
## 请参阅  
 [范围](../cpp/scope-visual-cpp.md)