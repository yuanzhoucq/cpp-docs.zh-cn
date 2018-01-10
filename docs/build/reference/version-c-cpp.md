---
title: "版本 （C/C + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VERSION
dev_langs: C++
helpviewer_keywords: VERSION .def file statement
ms.assetid: 3533b97c-5183-45f9-9ca8-4e63462b5d26
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 63ea65a8e3732ee17cc30b3382aa7ebc56e48f59
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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