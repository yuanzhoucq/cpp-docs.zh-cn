---
title: 链接器工具警告 LNK4105 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4105
dev_langs:
- C++
helpviewer_keywords:
- LNK4105
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ffdd8953e08f38d36bdfc2e68ad6cb8e06fb85b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33304409"
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