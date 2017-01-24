---
title: "链接器工具警告 LNK4105 | Microsoft Docs"
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
  - "LNK4105"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4105"
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具警告 LNK4105
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不存在用选项“option”指定的参数；将忽略选项  
  
 仅当设置了 [\/LIBPATH](../../build/reference/libpath-additional-libpath.md) 选项时才出现此警告。  如果使用此选项没有指定任何目录，链接器将忽略该选项并生成此警告消息。  
  
 如果不想重写现有环境库设置，请将 \/LIBPATH 选项从链接器命令行中移除。  如果想使用库的备用搜索路径，请在 \/LIBPATH 选项的后面指定备用路径。  
  
## 示例  
  
```  
link /libpath:c:\filepath\lib bar.obj  
```  
  
 指示链接器在搜索默认位置之前在 `c:\filepath\lib` 中搜索所需的库。