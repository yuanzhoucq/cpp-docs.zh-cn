---
title: "库 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LIBRARY
dev_langs:
- C++
helpviewer_keywords:
- LIBRARY .def file statement
ms.assetid: 1d7ccc92-e088-4ef7-9ef0-25c3862cc051
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 71637c83eda0ee641a4b66d94ba113162baa7bf2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="library"></a>LIBRARY
告知链接以创建 DLL。 同时，LINK 将创建导入库，除非在生成中使用了.exp 文件。  
  
```  
LIBRARY [library][BASE=address]  
```  
  
## <a name="remarks"></a>备注  
 *库*参数指定的 DLL 的名称。 你还可以使用[/out](../../build/reference/out-output-file-name.md)链接器选项以指定 DLL 的输出名称。  
  
 基 =*地址*参数设置操作系统用来加载 DLL 的基址。 此参数将覆盖 0x10000000 的默认 DLL 位置。 请参阅说明[/base](../../build/reference/base-base-address.md)有关基址的详细信息的选项。  
  
 请记住使用[/DLL](../../build/reference/dll-build-a-dll.md)链接器选项生成 DLL。  
  
## <a name="see-also"></a>请参阅  
 [模块定义语句的规则](../../build/reference/rules-for-module-definition-statements.md)