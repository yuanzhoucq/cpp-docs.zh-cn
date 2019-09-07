---
title: _callnewh
ms.date: 11/04/2016
apiname:
- _callnewh
apilocation:
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
apitype: DLLExport
f1_keywords:
- _callnewh
helpviewer_keywords:
- _callnewh
ms.assetid: 4dcb73e9-6384-4d12-a973-a8807d4de7a8
ms.openlocfilehash: 98526f6c8c40b71104345563db71ef098b6cfb8d
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739823"
---
# <a name="_callnewh"></a>_callnewh

调用当前已安装的*新处理程序*。

## <a name="syntax"></a>语法

```cpp
int _callnewh(
   size_t size
   )
```

### <a name="parameters"></a>参数

*size*<br/>
[新运算符](../../cpp/new-operator-cpp.md)尝试进行分配的内存量。

## <a name="return-value"></a>返回值

|值|Description|
|-----------|-----------------|
|0|否则要么没有安装新的处理程序，要么没有活动的新处理程序。|
|1|辉煌新处理程序已安装并处于活动状态。 可以重试内存分配。|

## <a name="exceptions"></a>Exceptions

如果找不到*新处理程序*，则此函数会引发 [bad_alloc](../../standard-library/bad-alloc-class.md)。

## <a name="remarks"></a>备注

如果[新运算符](../../cpp/new-operator-cpp.md)未能成功分配内存，则会调用*新处理程序*。 新处理程序随后会启动一些适当的操作，如释放内存，以便成功进行后续分配。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|_callnewh|internal.h|

## <a name="see-also"></a>请参阅

[_set_new_handler](set-new-handler.md)<br/>
[_set_new_mode](set-new-mode.md)<br/>
