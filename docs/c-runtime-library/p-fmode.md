---
title: __p__fmode
ms.date: 4/2/2020
api_name:
- __p__fmode
- _o___p__fmode
api_location:
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __p__fmode
helpviewer_keywords:
- __p__fmode
ms.assetid: 1daa1394-81eb-43aa-a71b-4cc6acf3207b
ms.openlocfilehash: dfd9962c49b03dbb30223d1d7403b791ed6dbec9
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919877"
---
# <a name="__p__fmode"></a>__p__fmode

指向 `_fmode` 全局变量，该变量为文件 I/O 操作指定默认的*文件转换模式*。

## <a name="syntax"></a>语法

```cpp
int* __p__fmode(
   );
```

## <a name="return-value"></a>返回值

指向 `_fmode` 全局变量的指针。

## <a name="remarks"></a>备注

`__p__fmode` 函数仅供内部使用，且不应从用户代码调用它。

文件转换模式为 [_open](../c-runtime-library/reference/open-wopen.md) 和 [_pipe](../c-runtime-library/reference/pipe.md) I/O 操作指定 `binary` 或 `text` 转换。 有关详细信息，请参阅 [_fmode](../c-runtime-library/fmode.md)。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|__p\__fmode|stdlib.h|
