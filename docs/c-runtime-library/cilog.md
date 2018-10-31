---
title: _CIlog |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _CIlog
apilocation:
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcrt.dll
apitype: DLLExport
f1_keywords:
- _CIlog
- CIlog
dev_langs:
- C++
helpviewer_keywords:
- _CIlog intrinsic
- CIlog intrinsic
ms.assetid: 23503854-ddaa-4fe0-a4a3-7fbb3a43bdec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3590ca4a9d7b5648c736c92d6a482377baa9ffa1
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235823"
---
# <a name="cilog"></a>_CIlog

计算堆栈顶部值的自然对数。

## <a name="syntax"></a>语法

```
void __cdecl _CIlog();
```

## <a name="remarks"></a>备注

此版本的 `log` 函数具有编译器理解的专用化调用约定。 它将加快执行的速度，因为它可防止生成副本和帮助注册表分配。

生成的值被将被推送到堆栈顶部。

## <a name="requirements"></a>要求

**平台：** x86

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[log、logf、log10、log10f](../c-runtime-library/reference/log-logf-log10-log10f.md)