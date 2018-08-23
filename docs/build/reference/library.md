---
title: 库 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- LIBRARY
dev_langs:
- C++
helpviewer_keywords:
- LIBRARY .def file statement
ms.assetid: 1d7ccc92-e088-4ef7-9ef0-25c3862cc051
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0d2fb7e69b0557bf96601666c390b3d59412b5a0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371159"
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