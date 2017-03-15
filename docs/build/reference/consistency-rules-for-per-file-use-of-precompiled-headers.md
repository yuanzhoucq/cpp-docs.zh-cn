---
title: "按文件使用预编译头的一致性规则 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pch 文件, 一致性规则"
  - "PCH 文件, 一致性规则"
  - "预编译的头文件, 一致性规则"
ms.assetid: afd49365-48bc-41f4-b700-fe8297b944a1
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 按文件使用预编译头的一致性规则
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[\/Yu](../../build/reference/yu-use-precompiled-header-file.md) 编译器选项允许指定要使用的预编译头 \(PCH\) 文件。  
  
 使用 PCH 时，除非另外指定，否则编译器将使用在创建 PCH 时有效的同一编译环境（使用一致的编译器选项、杂注等）。  如果编译器检测到不一致性，它将发出警告并在其可能出现的地方标识该不一致性。  这些警告不一定表明 PCH 有问题；它们只是警告您可能存在冲突。  下面几节介绍 PCH 的一致性要求。  
  
## 编译器选项一致性  
 使用 PCH 时，下列编译器选项可触发不一致性警告：  
  
-   使用“预处理器”\(\/D\) 选项创建的宏在创建 PCH 的编译与当前编译之间必须相同。  不检查已定义常数的状态，但如果这些常数改变，则可能发生不可预知的结果。  
  
-   PCH 不适用于 \/E 和 \/EP 选项。  
  
-   必须使用“生成浏览信息”\(\/FR\) 选项或“排除局部变量”\(\/Fr\) 选项创建了 PCH 后，后面使用 PCH 的编译才能使用这些选项。  
  
## C 7.0 兼容 \(\/Z7\)  
 如果在创建 PCH 时此选项生效，则后面使用 PCH 的编译可以使用调试信息。  
  
 如果在创建 PCH 时“与 C 7.0 兼容”\(\/Z7\)选项无效，则后面使用该 PCH 和 \/Z7 的编译将触发警告。  调试信息放置在当前的 .obj 文件中，并且 PCH 中定义的本地符号对调试器不可用。  
  
## 包含路径一致性  
 PCH 不包含有关在创建该 PCH 时有效的包含路径的信息。  使用 .pch 文件时，编译器总是使用当前编译中指定的包含路径。  
  
## 源文件一致性  
 指定“使用预编译头文件”\(\/Yu\) 选项时，编译器将忽略所有出现在要预编译的源代码中的预处理器指令（包括杂注）。  由这些预处理器指令指定的编译必须与用于“创建预编译头文件”\(\/Yc\) 选项的编译相同。  
  
## 杂注一致性  
 在创建 PCH 的过程中处理的杂注通常会影响后面与 PCH 一起使用的文件。  注释杂注和消息杂注不影响编译的其余部分。  
  
 下列杂注保留为 PCH 的一部分，并影响使用 PCH 的编译的其余部分。  
  
||||  
|-|-|-|  
|alloc\_text|include\_alias|pack|  
|auto\_inline|init\_seg|pointers\_to\_members|  
|check\_stack|inline\_depth|setlocale|  
|code\_seg|inline\_recursion|vtordisp|  
|data\_seg|intrinsic|warning|  
|function|optimize||  
  
## 请参阅  
 [预编译头一致性规则](../../build/reference/precompiled-header-consistency-rules.md)   
 [\/Yu（使用预编译的头文件）](../../build/reference/yu-use-precompiled-header-file.md)   
 [编译器选项](../../build/reference/compiler-options.md)