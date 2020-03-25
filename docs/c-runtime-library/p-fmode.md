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
ms.openlocfilehash: 2364a22d52c5bc418e4499a4a639c8e06559063a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171445"
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

文件转换模式为 `binary`_open`text` 和 [_pipe](../c-runtime-library/reference/open-wopen.md) I/O 操作指定 [ 或 ](../c-runtime-library/reference/pipe.md) 转换。 有关详细信息，请参阅 [_fmode](../c-runtime-library/fmode.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|__p\__fmode|stdlib.h|
