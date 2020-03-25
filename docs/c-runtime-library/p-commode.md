---
title: __p__commode
ms.date: 11/04/2016
api_name:
- __p__commode
api_location:
- msvcr110.dll
- msvcrt.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __p__commode
helpviewer_keywords:
- __p__commode
ms.assetid: 4380acb8-e3e4-409c-a60f-6205ac5189ce
ms.openlocfilehash: e3121c127c3ebf0f5fccdeb7ae0f67d0164d0965
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171471"
---
# <a name="__p__commode"></a>__p__commode

指向 `_commode` 全局变量，该变量为文件 I/O 操作指定默认的*文件提交模式*。

## <a name="syntax"></a>语法

```cpp
int * __p__commode(
   );
```

## <a name="return-value"></a>返回值

指向 `_commode` 全局变量的指针。

## <a name="remarks"></a>备注

`__p__commode` 函数仅供内部使用，且不应从用户代码调用它。

文件提交模式指定关键数据写入到磁盘的时间。 有关详细信息，请参阅 [fflush](../c-runtime-library/reference/fflush.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|__p\__commode|internal.h|
