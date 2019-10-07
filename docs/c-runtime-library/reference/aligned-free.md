---
title: _aligned_free
ms.date: 11/04/2016
api_name:
- _aligned_free
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-heap-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- aligned_free
- _aligned_free
helpviewer_keywords:
- _aligned_free function
- aligned_free function
ms.assetid: ed1ce952-cdfc-4682-85cc-f75d4101603d
ms.openlocfilehash: 44556d3f044a567f4903ef14a4b2a9b353af02ff
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943973"
---
# <a name="_aligned_free"></a>_aligned_free

释放使用 [_aligned_malloc](aligned-malloc.md) 或 [_aligned_offset_malloc](aligned-offset-malloc.md) 分配的内存块。

## <a name="syntax"></a>语法

```C
void _aligned_free (
   void *memblock
);
```

### <a name="parameters"></a>参数

*memblock*<br/>
指向返回到 `_aligned_malloc` 或 `_aligned_offset_malloc` 函数的内存块的指针。

## <a name="remarks"></a>备注

**_aligned_free**已标记`__declspec(noalias)`，这意味着该函数不能修改全局变量。 有关详细信息，请参阅 [noalias](../../cpp/noalias.md)。

此函数不会验证其参数，这与其他 _aligned CRT 函数不同。 如果*memblock*为 NULL 指针，则此函数只不执行任何操作。 它不会更改 `errno`，也不会调用无效的参数处理程序。 如果由于未使用先前分配内存块的 _aligned 函数或者由于一些不可预见的灾难而使内存不一致，从而导致函数中出现错误，函数将从 [_RPT、_RPTF、_RPTW、_RPTFW 宏](rpt-rptf-rptw-rptfw-macros.md)生成调试报告。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_aligned_free**|\<malloc.h>|

## <a name="example"></a>示例

有关详细信息，请参阅 [_aligned_malloc](aligned-malloc.md)。

## <a name="see-also"></a>请参阅

[数据对齐](../../c-runtime-library/data-alignment.md)