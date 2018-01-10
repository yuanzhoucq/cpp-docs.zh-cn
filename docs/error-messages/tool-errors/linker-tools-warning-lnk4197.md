---
title: "链接器工具警告 LNK4197 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4197
dev_langs: C++
helpviewer_keywords: LNK4197
ms.assetid: 8a976fd7-a74b-4c83-ab66-a9e7d7073c4a
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b1fadbf2ba5b18004f0e89142c88a68437842a92
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4197"></a>链接器工具警告 LNK4197
导出 exportname 指定了多次;使用第一种规范  
  
 导出指定在多个不同的方式。 链接器使用的第一个规范而忽略其余。  
  
 如果你正在重新生成的 C 运行时库，你可以忽略此消息。  
  
 如果导出多次指定相同的方式，链接器将不会发出警告。  
  
 例如，一个.def 文件的以下内容将会导致此警告：  
  
```  
EXPORTS  
   functioname      NONAME  
   functioname      @10  
```  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复  
  
1.  指定同一个导出命令行上 (通过导出:) 和.def 文件  
  
2.  同一个导出两次列入.def 文件具有不同的属性。