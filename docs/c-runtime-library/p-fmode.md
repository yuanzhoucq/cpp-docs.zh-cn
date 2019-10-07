---
title: __p__fmode
ms.date: 11/04/2016
api_name:
- __p__fmode
api_location:
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __p__fmode
helpviewer_keywords:
- __p__fmode
ms.assetid: 1daa1394-81eb-43aa-a71b-4cc6acf3207b
ms.openlocfilehash: 6f7676fc5c9958be3d0567e6bf22a11367094150
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939988"
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

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|__p\__fmode|stdlib.h|