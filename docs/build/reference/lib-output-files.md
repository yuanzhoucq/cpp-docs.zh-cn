---
title: LIB 输出文件 |Microsoft Docs
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
- output files, LIB
ms.assetid: e73d2f9b-a42d-402b-b7e3-3a94bebb317e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 23665897266bab87c71b8b3889688113fe8aa99a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720702"
---
# <a name="lib-output-files"></a>LIB 输出文件

LIB 所产生的输出文件取决于在其中它的使用的模式下, 表中所示。

|模式|输出|
|----------|------------|
|默认值 （构建或修改一个库）|COFF 库 (.lib)|
|提取与 /EXTRACT 成员|对象 (.obj) 文件|
|生成导出文件并导入使用 /DEF 库|导入库 (.lib) 和导出 (.exp) 文件|

## <a name="see-also"></a>请参阅

[LIB 概述](../../build/reference/overview-of-lib.md)