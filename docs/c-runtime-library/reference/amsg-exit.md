---
title: _amsg_exit
ms.date: 11/04/2016
api_name:
- _amsg_exit
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _amsg_exit
helpviewer_keywords:
- _amsg_exit
ms.assetid: 146d4faf-d763-43a4-b264-12711196456b
ms.openlocfilehash: 31979a3181dc57644f1e6877277884e55cebf733
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170926"
---
# <a name="_amsg_exit"></a>_amsg_exit

发出指定的运行时错误消息，然后退出应用程序，错误代码为 255。

## <a name="syntax"></a>语法

```cpp
void _amsg_exit ( int rterrnum );
```

### <a name="parameters"></a>parameters

*rterrnum*<br/>
系统定义的运行时错误消息的标识号。

## <a name="remarks"></a>备注

此函数会向控制台应用程序的 **stderr** 发出运行时错误消息，或在 Windows 应用程序的消息框中显示该消息。 在调试模式下，您可以选择在退出之前调用调试器。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|_amsg_exit|internal.h|
