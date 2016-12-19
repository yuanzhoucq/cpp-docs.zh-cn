---
title: "编译器警告（等级 1）C4397 | Microsoft Docs"
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
  - "C4397"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4397"
ms.assetid: 6346fdc2-dbbf-4fba-803a-32b0d0a707be
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4397
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

已忽略 DefaultCharSetAttribute  
  
 <xref:System.Runtime.InteropServices.DefaultCharSetAttribute> 已由 Visual C\+\+ 编译器忽略。  要指定 DLL 的字符集，请使用 DllImport 的 CharSet 选项。  有关详细信息，请参阅[使用 C\+\+ 互操作（隐式 PInvoke）](../../dotnet/using-cpp-interop-implicit-pinvoke.md)。  
  
## 示例  
 下面的示例生成 C4397。  
  
```  
// C4397.cpp  
// compile with: /W1 /c /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
[module:DefaultCharSetAttribute(CharSet::Unicode)];   // C4397  
  
[DllImport("kernel32", EntryPoint="CloseHandle", CharSet=CharSet::Unicode)]   // OK  
extern "C" bool ImportDefault(IntPtr hObject);  
  
public ref class MySettingVC {  
public:  
   void method() {  
      ImportDefault(IntPtr::Zero);  
   }  
};  
  
[StructLayout(LayoutKind::Explicit)]  
public ref struct StructDefault1{};  
  
public ref class ClassDefault1{};  
```