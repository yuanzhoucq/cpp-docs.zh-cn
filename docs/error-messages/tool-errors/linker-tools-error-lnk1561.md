---
title: "链接器工具错误 LNK1561 | Microsoft Docs"
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
  - "LNK1561"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1561"
ms.assetid: cb0b709b-7c9c-4496-8a4e-9e1e4aefe447
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具错误 LNK1561
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

必须定义入口点  
  
 链接器未找到入口点。  您可能打算作为 DLL 进行链接，在此情况下应使用 [\/DLL](../../build/reference/dll-build-a-dll.md) 选项进行链接。  您也可能忘记了指定入口点的名称；请使用 [\/ENTRY](../../build/reference/entry-entry-point-symbol.md) 选项进行链接。  
  
 否则，应在代码中包含 main、wmain、WinMain 或 wMain 函数。  
  
 如果您正使用 [LIB](../../build/reference/lib-reference.md) 并想要生成 .dll，出现此错误的一个原因是提供了 .def 文件。  如果是这样，从该生成中移除 .def 文件。  
  
 下面的示例生成 LNK1561：  
  
```  
// LNK1561.cpp  
// LNK1561 expected  
int i;  
// add a main function to resolve this error  
```