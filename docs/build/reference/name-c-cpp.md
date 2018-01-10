---
title: "名称 （C/C + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: name
dev_langs: C++
helpviewer_keywords: NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 33e81f63e7647cbdbdc89b37ffdcb309b79e9340
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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