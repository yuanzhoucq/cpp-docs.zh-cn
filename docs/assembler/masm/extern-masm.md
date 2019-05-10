---
title: EXTERN (MASM)
ms.date: 08/30/2018
f1_keywords:
- extern
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
ms.openlocfilehash: 30d1b3ae7c6676aeb97b91c7627da859525b9ce1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62203610"
---
# <a name="extern-masm"></a>EXTERN (MASM)

定义一个或多个外部变量、 标签或符号名为*名称*其类型是*类型*。

## <a name="syntax"></a>语法

> EXTERN [[*langtype*]] *name* [[ (*altid*) ]] : *type* [[, [[*langtype*]] *name* [[ (*altid*) ]] : *type*]] ...

## <a name="remarks"></a>备注

*类型*可以是[ABS](../../assembler/masm/operator-abs.md)，它导入*名称*为常量。 与相同[EXTRN](../../assembler/masm/extrn.md)。

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>