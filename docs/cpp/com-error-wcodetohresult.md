---
title: _com_error::WCodeToHRESULT
ms.date: 11/04/2016
f1_keywords:
- _com_error::WCodeToHRESULT
helpviewer_keywords:
- WCodeToHRESULT method [C++]
ms.assetid: 0ec43a4b-ca91-42d5-b270-3fde9c8412ea
ms.openlocfilehash: f2fc84be53d95754d21c30eaea8dd981447453d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593048"
---
# <a name="comerrorwcodetohresult"></a>_com_error::WCodeToHRESULT

**Microsoft 专用**

映射 16 位*wCode*为 32 位 HRESULT。

## <a name="syntax"></a>语法

```
static HRESULT WCodeToHRESULT(
   WORD wCode
) throw( );
```

#### <a name="parameters"></a>参数

*WCode*<br/>
16 位*wCode*要映射到 32 位的 HRESULT。

## <a name="return-value"></a>返回值

映射从 16 位的 32 位 HRESULT *wCode*。

## <a name="remarks"></a>备注

请参阅[WCode](../cpp/com-error-wcode.md)成员函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)<br/>
[_com_error 类](../cpp/com-error-class.md)