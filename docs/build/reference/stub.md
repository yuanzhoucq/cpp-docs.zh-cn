---
title: 存根 （STUB) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- STUB
dev_langs:
- C++
helpviewer_keywords:
- STUB .def file statement
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 385e073f877a938a3b73fa79036d27cf50c1e4ec
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="stub"></a>STUB
生成虚拟设备驱动程序 (VxD) 的模块定义文件中使用时，允许你指定的文件名称包含 IMAGE_DOS_HEADER 结构结构 （在 WINNT 中定义。H) 用于虚拟设备驱动程序 (VxD)，而不是默认标头。  
  
```  
STUB:filename  
```  
  
## <a name="remarks"></a>备注  
 另一种方法指定*filename*与[/存根](../../build/reference/stub-ms-dos-stub-file-name.md)链接器选项。  
  
 存根是有效的模块定义文件中仅在生成 VxD 时。  
  
## <a name="see-also"></a>请参阅  
 [模块定义语句的规则](../../build/reference/rules-for-module-definition-statements.md)