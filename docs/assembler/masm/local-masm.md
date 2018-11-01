---
title: LOCAL (MASM)
ms.date: 08/30/2018
f1_keywords:
- Local
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
ms.openlocfilehash: c8ea49b9862159a5a56bfb3d2c3cd0c1f4cd7413
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596867"
---
# <a name="local-masm"></a>LOCAL (MASM)

中的第一个指令，宏，内部**本地**定义宏的每个实例是唯一的标签。

## <a name="syntax"></a>语法

> 本地*localname* [[， *localname*]]...

> 本地*标签*[[[*计数*]]] [[:*类型*]] [[，*标签*[[[*计数*]]] [[*类型*]]]]...

## <a name="remarks"></a>备注

在过程定义中的第二个指令 (**PROC**)，**本地**创建过程的持续期间存在的基于堆栈的变量。 *标签*可以是简单的变量或一个数组，包含*计数*元素。

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>