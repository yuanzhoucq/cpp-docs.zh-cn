---
title: LIB 输入文件 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- Lib
dev_langs:
- C++
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 140a0f1d9ef6fdb3ca5e6d6977804684c88af1fb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="lib-input-files"></a>LIB 输入文件
LIB 所需的输入的文件取决于在其中它的使用的模式下, 表中所示。  
  
|模式|输入|  
|----------|-----------|  
|默认值 （生成或修改库）|COFF 对象 (.obj) 文件，COFF 库 (.lib)，32 位对象模型格式 (OMF) 对象 (.obj) 文件|  
|提取与 /extract، 成员|COFF 库 (.lib)|  
|生成导出文件和导入具有 /DEF 库|模块定义 (.def) 文件、 COFF 对象 (.obj) 文件、 COFF 库 (.lib)、 32 位 OMF 对象 (.obj) 文件|  
  
> [!NOTE]
>  OMF 库创建的 LIB 的 16 位版本不能为 LIB 的 32 位版本的输入。  
  
## <a name="see-also"></a>请参阅  
 [LIB 概述](../../build/reference/overview-of-lib.md)