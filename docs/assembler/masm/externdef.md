---
title: EXTERNDEF
ms.date: 08/30/2018
f1_keywords:
- EXTERNDEF
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
ms.openlocfilehash: 23d34af470e825a8535de8cb28645a7bfb4c4d1b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619760"
---
# <a name="externdef"></a>EXTERNDEF

定义一个或多个外部变量、 标签或符号名为*名称*其类型是`type`。

## <a name="syntax"></a>语法

> EXTERNDEF [langtype 名称： 类型 [[，[langtype 名称： 键入]]...

## <a name="remarks"></a>备注

如果*名称*定义在模块中，它被视为[公共](../../assembler/masm/public-masm.md)。 如果*名称*引用在模块中，它被视为[EXTERN](../../assembler/masm/extern-masm.md)。 如果*名称*是它未被引用，将被忽略。 `type`可以是[ABS](../../assembler/masm/operator-abs.md)，它导入*名称*为常量。 通常用于在包含文件。

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>