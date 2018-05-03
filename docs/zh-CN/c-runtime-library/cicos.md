---
title: _CIcos |Microsoft 文档
ms.custom: ''
ms.date: 04/11/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CIcos
apilocation:
- msvcr90.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- CIcos
- _CIcos
dev_langs:
- C++
helpviewer_keywords:
- _CIcos intrinsic
- CIcos intrinsic
ms.assetid: 6fc203fb-66f3-4ead-9784-f85833c26f1b
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cb399a25bacd7fc288ad881625589e240009068a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
---
# <a name="cicos"></a>_CIcos

计算浮点堆栈顶部值的余弦值。

## <a name="syntax"></a>语法

```C
void __cdecl _CIcos();
```

## <a name="remarks"></a>备注

此版本的 [cos](../c-runtime-library/reference/cos-cosf-cosl.md) 函数具有编译器理解的专用化调用约定。 它将加快执行的速度，因为它可防止生成副本和帮助注册表分配。

生成的值被将被推送到浮点堆栈顶部。

## <a name="requirements"></a>惠?

**平台：**x86

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[cos、cosf、cosl](../c-runtime-library/reference/cos-cosf-cosl.md)<br/>
