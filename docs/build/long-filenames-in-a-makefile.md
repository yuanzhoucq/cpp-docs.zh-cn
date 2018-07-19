---
title: 生成文件中的长文件名 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, long filenames
- long filenames
ms.assetid: 626d56fc-8879-46ba-9c2d-dd386c78cccc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc199289f80e6ce2f9dbc5317ee439af528a055b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367623"
---
# <a name="long-filenames-in-a-makefile"></a>生成文件中的长文件名
将长文件名用双引号括起来，如下所示：  
  
```  
all : "VeryLongFileName.exe"  
```  
  
## <a name="see-also"></a>请参阅  
 [生成文件的内容](../build/contents-of-a-makefile.md)