---
title: -ALLOWISOLATION |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ALLOWISOLATION
dev_langs:
- C++
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5cb92a7f31d48dad4a7fb608703c71ccc661e176
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368969"
---
# <a name="allowisolation"></a>/ALLOWISOLATION
指定清单查找的行为。  
  
## <a name="syntax"></a>语法  
  
```  
  
/ALLOWISOLATION[:NO]  
```  
  
## <a name="remarks"></a>备注  
 **/ALLOWISOLATION**会导致操作系统进行清单查找和加载。  
  
 **/ALLOWISOLATION**是默认设置。  
  
 **/ALLOWISOLATION:NO**该值指示像没有任何清单和原因加载可执行文件[EDITBIN 参考](../../build/reference/editbin-reference.md)设置`IMAGE_DLLCHARACTERISTICS_NO_ISOLATION`optional 标头中位`DllCharacteristics`字段。  
  
 当对可执行文件禁用隔离时，Windows 加载程序不会尝试为新创建的进程查找应用程序清单。 新的进程没有默认激活上下文，即使当在可执行文件本身中的清单，或者如果没有清单，其名称*可执行文件名称*。 exe.manifest。  
  
## <a name="see-also"></a>请参阅  
 [EDITBIN 选项](../../build/reference/editbin-options.md)   
 [/ALLOWISOLATION （清单查找）](../../build/reference/allowisolation-manifest-lookup.md)   
 [清单文件引用](http://msdn.microsoft.com/library/aa375632.aspx)