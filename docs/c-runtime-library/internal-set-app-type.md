---
title: __set_app_type
ms.date: 11/04/2016
api_name:
- __set_app_type
- _set_app_type
api_location:
- msvcr90.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __set_app_type
helpviewer_keywords:
- __set_app_type
ms.assetid: f0ac0f4d-70e6-4e96-9e43-eb9d1515490c
ms.openlocfilehash: 8efe2159618f728cfaad33493dd482fbdd5375f7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171484"
---
# <a name="__set_app_type"></a>__set_app_type

设置当前应用程序类型。

## <a name="syntax"></a>语法

```cpp
void __set_app_type (
   int at
   )
```

#### <a name="parameters"></a>parameters

*at*<br/>
表示应用程序类型的值。 可能的值包括：

|值|说明|
|-----------|-----------------|
|_UNKNOWN_APP|未知应用程序类型。|
|_CONSOLE_APP|控制台（命令行）应用程序。|
|_GUI_APP|GUI (Windows) 应用程序。|

## <a name="remarks"></a>备注

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|__set_app_type|internal.h|
