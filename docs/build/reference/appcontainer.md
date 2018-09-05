---
title: -APPCONTAINER |Microsoft Docs
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
ms.openlocfilehash: ea6f08a141d48183d96dba6cb02fcf31909af0ae
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43686248"
---
# <a name="appcontainer"></a>/APPCONTAINER
标记必须在应用程序容器中运行的可执行文件 — 例如，一个 Microsoft Store 或通用 Windows 应用。  
  
```  
  
/APPCONTAINER[:NO]  
```  
  
## <a name="remarks"></a>备注  
 设置了 **/APPCONTAINER** 选项的可执行文件只能在应用容器中运行，应用容器是 Windows 8 中引入的进程隔离环境。 对于 Microsoft Store 和通用 Windows 应用，必须设置此选项。  
  
## <a name="see-also"></a>请参阅  
 [EDITBIN 选项](../../build/reference/editbin-options.md)   
 [什么是通用 Windows 应用？](/windows/uwp/get-started/universal-application-platform-guide)