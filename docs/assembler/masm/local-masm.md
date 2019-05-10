---
title: LOCAL (MASM)
ms.date: 08/30/2018
f1_keywords:
- Local
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
ms.openlocfilehash: 94af498865151ff5c49fac9dbc03de65c4ecb934
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62178002"
---
# <a name="local-masm"></a>LOCAL (MASM)

中的第一个指令，宏，内部**本地**定义宏的每个实例是唯一的标签。

## <a name="syntax"></a>语法

> 本地*localname* \[， *localname*]...
>
> 本地*标签* \[ __\[__*计数*__]__ ] \[ __:__ *类型*] \[ __，__ *标签* \[ __\[__*计数*__]__ ] \[*类型*]]...

## <a name="remarks"></a>备注

在过程定义中的第二个指令 (**PROC**)，**本地**创建过程的持续期间存在的基于堆栈的变量。 *标签*可以是简单的变量或一个数组，包含*计数*元素。

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>