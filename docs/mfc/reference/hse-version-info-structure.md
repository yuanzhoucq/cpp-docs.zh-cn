---
title: HSE_VERSION_INFO 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- HSE_VERSION_INFO
dev_langs:
- C++
helpviewer_keywords:
- HSE_VERSION_INFO structure [MFC]
ms.assetid: 4837312d-68c8-4d05-9afa-1934d7d49b20
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 08b16c59f155864a781feccbfd08842380cccd01
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433791"
---
# <a name="hseversioninfo-structure"></a>HSE_VERSION_INFO 结构

此结构所指向的*pVer*中的参数`CHttpServer::GetExtensionVersion`成员函数。 它提供 ISA 的 ISA 版本号和文本说明。

## <a name="syntax"></a>语法

```
typedef struct _HSE_VERSION_INFO {
    DWORD dwExtensionVersion;
    CHAR lpszExtensionDesc[HSE_MAX_EXT_DLL_NAME_LEN];
} HSE_VERSION_INFO, *LPHSE_VERSION_INFO;
```

#### <a name="parameters"></a>参数

*dwExtensionVersion*<br/>
ISA 版本号

*lpszExtensionDesc*<br/>
ISA 的文本说明。 默认实现提供占位符文本；重写 `CHttpServer::GetExtensionVersion` 可提供您自己的说明。

## <a name="requirements"></a>要求

**标头：** httpext.h

## <a name="see-also"></a>请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

