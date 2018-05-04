---
title: 版本 （C/C + +） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VERSION
dev_langs:
- C++
helpviewer_keywords:
- VERSION .def file statement
ms.assetid: 3533b97c-5183-45f9-9ca8-4e63462b5d26
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fcaf4e113af6182a2d3d735e4c668b62336e2c79
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="version-cc"></a>VERSION (C/C++)
通知链接以.exe 文件的标头中放置一个数字或 DLL。  
  
```  
VERSION major[.minor]  
```  
  
## <a name="remarks"></a>备注  
 *主要*和*次要*自变量为十进制数字 0 到 65535 的范围。 默认值为 0.0 版。  
  
 指定的版本号的等效方法是使用[版本信息](../../build/reference/version-version-information.md)(/ 版本) 选项。  
  
## <a name="see-also"></a>请参阅  
 [模块定义语句的规则](../../build/reference/rules-for-module-definition-statements.md)