---
title: "链接器工具错误 LNK1112 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1112"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1112"
ms.assetid: 425793d8-37e6-4072-9b6e-c3d4e9c12562
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# 链接器工具错误 LNK1112
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

模块计算机类型“type1”与目标计算机类型“type2”冲突  
  
 指定为输入的对象文件为不同的计算机类型进行了编译。  
  
 例如，如果你尝试链接使用 **\/clr** 编译的对象文件和使用 **\/clr:pure**（计算机类型 CEE）编译的对象文件，则链接器将生成错误 LNK1112。  
  
 同样，如果你使用 [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] 编译器创建一个模块并使用 x86 编译器创建另一个模块，然后尝试链接它们，那么链接器将生成 LNK1112。  
  
 此错误的可能原因是你正在开发 64 位应用程序但未安装其中一个 Visual C\+\+ 64 位编译器。 在这种情况下，64 位配置将不可用。 若要解决此问题，运行 Visual Studio 的安装程序并安装缺少的 C\+\+ 组件。  
  
 在删除中间项目文件前，如果你在“配置管理器”中更改“活动解决方案配置”，然后尝试生成项目也会发生此错误。 若要解决此错误，请从“生成”菜单选择“重新生成解决方案”。 还可从“生成”菜单选择“清理解决方案”，然后生成解决方案。  
  
## 请参阅  
 [链接器工具错误和警告](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)