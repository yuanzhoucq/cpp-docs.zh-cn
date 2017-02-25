---
title: "__debugbreak | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__debugbreak_cpp"
  - "__debugbreak"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__debugbreak 内部"
  - "断点, __debugbreak 内部"
ms.assetid: 1d1e1c0c-891a-4613-ae4b-d790094ba830
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# __debugbreak
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 将在代码中引起断点，并在其中提示用户运行调试程序。  
  
## 语法  
  
```  
void __debugbreak();  
```  
  
## 要求  
  
|内部函数|体系结构|Header|  
|----------|----------|------------|  
|`__debugbreak`|x86、ARM、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h\>|  
  
## 备注  
 `__debugbreak` 编译器内部函数（类似于 [DebugBreak](http://msdn.microsoft.com/library/windows/desktop/ms679297.aspx)）是一种用于引起断点的可移植 Win32 方式。  
  
> [!NOTE]
>  编译 **\/clr** 时，会将包含 `__debugbreak` 的函数编译到 MSIL。  `asm int 3` 可将函数编译为本机函数。  有关详细信息，请参阅[\_\_asm](../assembler/inline/asm.md)。  
  
 例如：  
  
```  
main() {  
   __debugbreak();  
}  
```  
  
 类似于：  
  
```  
main() {  
   __asm {  
      int 3  
   }  
}  
```  
  
 在 x86 计算机上。  
  
 此例程仅可用作内部函数。  
  
## 结束 Microsoft 专用  
  
## 请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)