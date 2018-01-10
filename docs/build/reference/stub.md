---
title: "存根 （STUB) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: STUB
dev_langs: C++
helpviewer_keywords: STUB .def file statement
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 58430f8211f8859b65103b53d1f98a173c4635ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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