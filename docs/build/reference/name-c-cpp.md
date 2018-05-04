---
title: 名称 （C/C + +） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- name
dev_langs:
- C++
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a94b82a65cf68d9802d7bf9620e4128ab6b35071
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="name-cc"></a>NAME (C/C++)
指定主输出文件的名称。  
  
```  
NAME [application][BASE=address]  
```  
  
## <a name="remarks"></a>备注  
 指定输出文件的名称的等效方法是使用[/out](../../build/reference/out-output-file-name.md)链接器选项和设置的基址等效的方法均由[/base](../../build/reference/base-base-address.md)链接器选项。 如果同时指定了，/扩展重写**名称**。  
  
 如果你生成 DLL，名称只会影响 DLL 名称。  
  
## <a name="see-also"></a>请参阅  
 [模块定义语句的规则](../../build/reference/rules-for-module-definition-statements.md)