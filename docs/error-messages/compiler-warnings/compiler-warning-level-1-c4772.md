---
title: "编译器警告（等级 1）C4772 | Microsoft Docs"
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
  - "C4772"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4772"
ms.assetid: dafe6fd8-9faf-41f5-9d66-a55838742c14
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4772
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#import 引用了缺少的类型库中的类型；“missing\_type”用作占位符  
  
 类型库是使用 [\#import](../../preprocessor/hash-import-directive-cpp.md) 指令引用的。  但是，类型库包含一个对另一类型库的引用，它不是使用 `#import` 引用的。  编译器没有找到此其他 .tlb 文件。  
  
 请注意，如果使用编译器选项 [\/I（附加包含目录）](../../build/reference/i-additional-include-directories.md) 指定这些目录，编译器将不在其他目录中查找类型库。  如果希望编译器在其他目录中查找类型库，请将这些目录添加到 PATH 环境变量中。  
  
 默认情况下，此警告作为错误发出。  不能用 \/W0 取消显示 C4772。  
  
## 示例  
 这是再现 C4772 所需的第一个类型库。  
  
```  
// c4772a.idl  
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]  
library C4772aLib  
{  
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c100")]  
   enum E_C4772a  
   {  
      one, two, three  
   };  
};  
```  
  
## 示例  
 这是再现 C4772 所需的第二个类型库。  
  
```  
// c4772b.idl  
// post-build command: del /f C4772a.tlb  
// C4772a.tlb is available when c4772b.tlb is built  
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]  
library C4772bLib  
{  
   importlib ("c4772a.tlb");  
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]  
   struct S_C4772b  
   {  
      enum E_C4772a e;  
   };  
};  
```  
  
## 示例  
 下面的示例生成 C4772：  
  
```  
// C4772.cpp  
// assumes that C4772a.tlb is not available to the compiler  
// #import "C4772a.tlb"  
#import "C4772b.tlb"   // C4772 uncomment previous line to resolve  
                       // and make sure c4772a.tlb is on disk  
```