---
title: "链接器工具警告 LNK4105 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4105
dev_langs: C++
helpviewer_keywords: LNK4105
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 913a6da056908def8df5aab1c2425ef9a187c1e2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4105"></a>链接器工具警告 LNK4105
使用选项 option; 指定任何自变量忽略选项  
  
 此警告时才会发生时[/LIBPATH](../../build/reference/libpath-additional-libpath.md)设置选项。 如果使用此选项不指定任何目录，链接器将忽略该选项，并且将生成此警告消息。  
  
 如果不需要重写现有环境库设置，请从链接器命令行删除 /LIBPATH 选项。 如果你想要用于库的备用搜索路径，指定 /LIBPATH 选项后面的备用路径。  
  
## <a name="example"></a>示例  
  
```  
link /libpath:c:\filepath\lib bar.obj  
```  
  
 将指示链接器为所需的库中搜索`c:\filepath\lib`之前在默认位置中搜索。