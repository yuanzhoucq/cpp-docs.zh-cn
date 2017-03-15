---
title: "编译器错误 C3809 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3809"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3809"
ms.assetid: 37eca584-c20c-464e-8e45-a987214b7ce4
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C3809
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class”: 托管或 WinRT 类型不能有任何友元函数\/类\/接口  
  
 托管类型和 Windows 运行时类型不允许使用友元。  若要修复此错误，请不要声明在托管或 Windows 运行时类型内声明友元。  
  
 下面的示例生成 C3809：  
  
```  
// C3809a.cpp  
// compile with: /clr  
ref class A {};  
  
ref class B  
{  
public:  
   friend ref class A;   // C3809  
};  
  
int main()  
{  
}  
```