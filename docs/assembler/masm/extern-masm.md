---
title: EXTERN (MASM)
ms.date: 08/30/2018
f1_keywords:
- extern
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
ms.openlocfilehash: 30d1b3ae7c6676aeb97b91c7627da859525b9ce1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497348"
---
# <a name="extern-masm"></a>EXTERN (MASM)

定义一个或多个外部变量、 标签或符号名为*名称*其类型是*类型*。

## <a name="syntax"></a>语法

> EXTERN [[*langtype*]]*名称*[[(*altid*)]]:*类型*[[，[[*langtype*]] *名称*[[(*altid*)]]:*类型*]]...

## <a name="remarks"></a>备注

*类型*可以是[ABS](../../assembler/masm/operator-abs.md)，它导入*名称*为常量。 与相同[EXTRN](../../assembler/masm/extrn.md)。

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>