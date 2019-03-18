---
title: LIB 输入文件
ms.date: 11/04/2016
f1_keywords:
- Lib
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
ms.openlocfilehash: 648871464dbc99972b8ca40579046347727e81cf
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808126"
---
# <a name="lib-input-files"></a>LIB 输入文件

LIB 所需的输入的文件取决于在其中它的使用的模式下, 表中所示。

|模式|输入|
|----------|-----------|
|默认值 （构建或修改一个库）|COFF 对象 (.obj) 文件，COFF 库 (.lib)，32 位对象模型格式 (OMF) 对象 (.obj) 文件|
|提取与 /EXTRACT 成员|COFF 库 (.lib)|
|生成导出文件并导入使用 /DEF 库|模块定义 (.def) 文件、 COFF 对象 (.obj) 文件、 COFF 库 (.lib)、 32 位 OMF 对象 (.obj) 文件|

> [!NOTE]
>  OMF 库创建的 LIB 的 16 位版本不能用作 LIB 的 32 位版本的输入。

## <a name="see-also"></a>请参阅

[LIB 概述](overview-of-lib.md)
