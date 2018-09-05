---
title: EXTERN (MASM) |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- extern
dev_langs:
- C++
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a9008e8c1153c0a9b06530b14e661436f7e62a9
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693665"
---
# <a name="extern-masm"></a>EXTERN (MASM)

定义一个或多个外部变量、 标签或符号名为*名称*其类型是*类型*。

## <a name="syntax"></a>语法

> EXTERN [[*langtype*]]*名称*[[(*altid*)]]:*类型*[[，[[*langtype*]] *名称*[[(*altid*)]]:*类型*]]...

## <a name="remarks"></a>备注

*类型*可以是[ABS](../../assembler/masm/operator-abs.md)，它导入*名称*为常量。 与相同[EXTRN](../../assembler/masm/extrn.md)。

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>