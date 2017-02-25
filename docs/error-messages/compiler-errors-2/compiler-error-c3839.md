---
title: "编译器错误 C3839 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3839"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3839"
ms.assetid: 0957faff-1e9f-439b-876b-85bd8d2c578d
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 编译器错误 C3839
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法更改托管或 WinRT 类型中的对齐方式  
  
 托管或 Windows 运行时类型中变量的对齐是由 CLR 或 Windows 运行时控制的，不能使用 [align](../../cpp/align-cpp.md) 进行修改。  
  
 下面的示例生成 C3839：  
  
```  
// C3839a.cpp  
// compile with: /clr  
ref class C  
{  
public:  
   __declspec(align(32)) int m_j; // C3839  
};  
  
int main()  
{  
}  
  
```