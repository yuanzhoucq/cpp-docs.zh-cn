---
title: "编译器错误 C3270 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3270"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3270"
ms.assetid: 70e6e76b-7415-48f5-a61e-2ed50caf08e4
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C3270
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“field”: FieldOffset 特性只能在 StructLayout\(Explicit\) 上下文中使用，在该情况下它是必需的  
  
 使用 [FieldOffset](frlrfSystemRuntimeInteropServicesFieldOffsetAttributeClassTopic) 标记了一个字段，仅在 [StructLayout](frlrfSystemRuntimeInteropServicesStructLayoutAttributeClassTopic) Explicit 生效时允许使用该属性。  
  
 下面的示例生成 C3270：  
  
```  
// C3270_2.cpp // compile with: /clr /c using namespace System::Runtime::InteropServices; [ StructLayout(LayoutKind::Sequential) ] // try the following line instead // [ StructLayout(LayoutKind::Explicit) ] public value struct MYUNION { [FieldOffset(0)] int a;   // C3270 // ... };  
```  
  
 下面的示例生成 C3270：  
  
```  
// C3270.cpp // compile with: /clr:oldSyntax /LD #using <mscorlib.dll> using namespace System::Runtime::InteropServices; [ StructLayout(LayoutKind::Sequential) ] // try the following line instead // [ StructLayout(LayoutKind::Explicit) ] public __value struct MYUNION { [FieldOffset(0)] int a;   // C3270 // ... };  
```