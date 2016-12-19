---
title: "链接器工具警告 LNK4204 | Microsoft Docs"
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
  - "LNK4204"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4204"
ms.assetid: 14adda20-0cbe-407b-90f6-9f81c93530e2
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具警告 LNK4204
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“filename”缺少引用模块的调试信息；正在链接对象，就像没有调试信息一样  
  
 .pdb 文件具有错误签名。  链接器将继续链接对象但不使用调试信息。  可能需要使用 [\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) 选项重新编译对象文件。  
  
 如果库中的某些对象引用不存在的文件，则会触发 LNK4204。  重新生成解决方案时可能会出现这种情况，例如，由于编译错误，某个对象文件被删除但未重新生成。  在这种情况下，用 **\/Z7** 或 **\/Fd** 进行编译，来更新对象以引用每个库的单个文件（不是默认的 .pdb 文件名）。有关详细信息，请参阅[\/Fd（程序数据库文件名）](../../build/reference/fd-program-database-file-name.md)。请确保每次在源控制系统中更新该 .pdb 后用库保存它。