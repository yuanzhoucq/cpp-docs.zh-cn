---
title: 本地 (MASM) |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- Local
dev_langs:
- C++
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e8105bc8168ce28d468a1378c5cf7889907a7c9f
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685058"
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