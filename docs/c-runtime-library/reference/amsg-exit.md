---
title: _amsg_exit | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _amsg_exit
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
apitype: DLLExport
f1_keywords:
- _amsg_exit
dev_langs:
- C++
helpviewer_keywords:
- _amsg_exit
ms.assetid: 146d4faf-d763-43a4-b264-12711196456b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dbb7f46bb4f3c942fd1c9e1a1d45c1ccf48739f7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392791"
---
# <a name="amsgexit"></a>_amsg_exit

发出指定的运行时错误消息，然后退出应用程序，错误代码为 255。

## <a name="syntax"></a>语法

```cpp
void _amsg_exit ( int rterrnum );
```

### <a name="parameters"></a>参数

*rterrnum*<br/>
系统定义的运行时错误消息的标识号。

## <a name="remarks"></a>备注

此函数会向控制台应用程序的 **stderr** 发出运行时错误消息，或在 Windows 应用程序的消息框中显示该消息。 在调试模式下，您可以选择在退出之前调用调试器。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|_amsg_exit|internal.h|