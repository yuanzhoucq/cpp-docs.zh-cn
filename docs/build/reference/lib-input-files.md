---
title: LIB 输入文件
ms.date: 11/04/2016
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
ms.openlocfilehash: de81f79eecf3fc73c02894747f4b97cb107cf892
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328231"
---
# <a name="lib-input-files"></a>LIB 输入文件

LIB 预期的输入文件取决于使用它的模式，如下表所示。

|“模式”|输入|
|----------|-----------|
|默认值（构建或修改库）|COFF 对象 （.obj） 文件、COFF 库 （.lib）、32 位对象模型格式 （OMF） 对象 （.obj） 文件|
|使用 /EXTRACT 提取成员|COFF 库 （.lib）|
|使用 /DEF 构建导出文件和导入库|模块定义 （.def） 文件、COFF 对象 （.obj） 文件、COFF 库 （.lib）、32 位 OMF 对象 （.obj） 文件|

> [!NOTE]
> 由 16 位版本的 LIB 创建的 OMF 库不能用作对 32 位版本的 LIB 的输入。

## <a name="see-also"></a>另请参阅

[LIB 概述](overview-of-lib.md)
