---
title: LIB 输出文件
ms.date: 11/04/2016
f1_keywords:
- Lib
helpviewer_keywords:
- output files, LIB
ms.assetid: e73d2f9b-a42d-402b-b7e3-3a94bebb317e
ms.openlocfilehash: d7a6352665f12307bfa54025a32f9f7b84311dac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269695"
---
# <a name="lib-output-files"></a>LIB 输出文件

LIB 所产生的输出文件取决于在其中它的使用的模式下, 表中所示。

|模式|Output|
|----------|------------|
|默认值 （构建或修改一个库）|COFF 库 (.lib)|
|提取与 /EXTRACT 成员|对象 (.obj) 文件|
|生成导出文件并导入使用 /DEF 库|导入库 (.lib) 和导出 (.exp) 文件|

## <a name="see-also"></a>请参阅

[LIB 概述](overview-of-lib.md)
