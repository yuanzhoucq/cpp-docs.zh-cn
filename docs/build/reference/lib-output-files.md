---
title: LIB 输出文件
ms.date: 11/04/2016
f1_keywords:
- Lib
helpviewer_keywords:
- output files, LIB
ms.assetid: e73d2f9b-a42d-402b-b7e3-3a94bebb317e
ms.openlocfilehash: 31c69a273d9f201046171ecc8889dda6e07328d6
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57419317"
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
