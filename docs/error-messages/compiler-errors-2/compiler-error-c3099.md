---
title: "Compiler Error C3099 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3099"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3099"
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Compiler Error C3099
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“关键字”：将 \[System::AttributeUsageAttribute\] 用于托管特性；将 \[Windows::Foundation::Metadata::AttributeUsageAttribute\] 用于 WinRT 特性  
  
 使用 <xref:System.AttributeUsageAttribute> 声明 **\/clr** 特性。  使用 `Windows::Foundation::Metadata::AttributeUsageAttribute` 声明 Windows 运行时特性。  
  
 有关 \/CLR 特性的详细信息，请参阅[用户定义的特性](../../windows/user-defined-attributes-cpp-component-extensions.md)。  有关 Windows 运行时中支持的特性，请参阅 [Windows.Foundation.Metadata 命名空间](http://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.aspx)  
  
## 示例  
 下面的示例生成 C3099，并演示如何修复此错误。  
  
```  
// C3099.cpp  
// compile with: /clr /c  
using namespace System;  
[usage(10)]   // C3099  
// try the following line instead  
// [AttributeUsageAttribute(AttributeTargets::All)]  
ref class A : Attribute {};  
```