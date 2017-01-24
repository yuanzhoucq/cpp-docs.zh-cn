---
title: "编译器错误 C3813 | Microsoft Docs"
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
  - "C3813"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3813"
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3813
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

属性声明只能在托管类型或 WinRT 类型的定义内出现  
  
 [property](../../misc/property.md) 只能在托管类型或 Windows 运行时类型中声明。  本机类型不支持 `property` 关键字。  
  
 下面的示例生成 C3813，并演示如何修复此错误：  
  
```  
// C3813.cpp  
// compile by using: cl /c /clr C3813.cpp  
class A  
{  
   property int Int; // C3813  
};  
  
ref class B  
{  
   property int Int; // OK - declared within managed type  
};  
```