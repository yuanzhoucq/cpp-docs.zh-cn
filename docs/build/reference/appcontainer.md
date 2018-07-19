---
title: -APPCONTAINER |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /APPCONTAINER
dev_langs:
- C++
helpviewer_keywords:
- APPCONTAINER editbin option
- -APPCONTAINER editbin option
- /APPCONTAINER editbin option
ms.assetid: 0ca4f1ec-c8de-4a37-b3e2-deda7af0bb88
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5c47154d7a5eddd26573612708462c0352da30ae
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368429"
---
# <a name="appcontainer"></a>/APPCONTAINER
将标记必须在应用程序容器中运行的可执行文件-例如，Microsoft 应用商店或通用 Windows 应用。  
  
```  
  
/APPCONTAINER[:NO]  
```  
  
## <a name="remarks"></a>备注  
 设置了 **/APPCONTAINER** 选项的可执行文件只能在应用容器中运行，应用容器是 Windows 8 中引入的进程隔离环境。 对于 Microsoft 应用商店和通用 Windows 应用程序，必须设置此选项。  
  
## <a name="see-also"></a>请参阅  
 [EDITBIN 选项](../../build/reference/editbin-options.md)   
 [什么是通用 Windows 应用？](http://go.microsoft.com/fwlink/p/?LinkID=522074)