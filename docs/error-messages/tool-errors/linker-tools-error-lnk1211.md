---
title: "链接器工具错误 LNK1211 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1211"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1211"
ms.assetid: 607400eb-4180-4892-817f-eedfa628af61
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 链接器工具错误 LNK1211
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未找到预编译类型信息；未链接或覆盖“filename”  
  
 在 LINK 命令中没有指定用 [\/Yc](../../build/reference/yc-create-precompiled-header-file.md) 编译的给定对象文件，或者该文件被覆盖了。  
  
 如果创建使用预编译头的调试库并且指定 \/Yc 和 [\/Z7](../../build/reference/z7-zi-zi-debug-information-format.md)，Visual C\+\+ 将生成包含 CodeView 调试信息的预编译对象文件。  只有当将预编译对象文件存储在库中，使用该库生成可执行图像，并且引用的对象文件没有对该预编译对象文件定义的任意函数的可传递引用时，才出现此错误。  
  
 有两种解决此问题的方法：  
  
-   指定 [\/Yd](../../build/reference/yd-place-debug-information-in-object-file.md) 编译器选项，以将预编译头的 CodeView 信息添加到每个对象模块中。  该方法不太可取，因为它通常产生大的对象模块，从而会增加链接应用程序所需的时间。  
  
-   在创建不包含任何函数定义的预编译头文件时，指定 [\/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md)，并传递任何任意字符串的名称。  这指示编译器在预编译对象文件中创建符号，并在每个使用与预编译对象文件关联的预编译头文件的对象文件中发出对该符号的引用。  
  
 当用 **\/Yc** 和 **\/Yl** 编译模块时，编译器创建类似于 `__@@_PchSym_@00@...@symbol_name` 的符号（其中的省略号 \(...\) 表示编译器生成的字符串），并将其存储在对象模块中。  用此预编译头编译的任何源文件都引用指定的符号，这导致链接器包括对象模块及其在库中的调试信息。  
  
 有关此错误的更多信息，请参见知识库文章 Q102697 PRB: Build Errors Using Precompiled Header in Debugging Lib。