---
title: _com_error::WCodeToHRESULT
ms.date: 11/04/2016
f1_keywords:
- _com_error::WCodeToHRESULT
helpviewer_keywords:
- WCodeToHRESULT method [C++]
ms.assetid: 0ec43a4b-ca91-42d5-b270-3fde9c8412ea
ms.openlocfilehash: f2194e0e54a93d3227b84d893f9d3f208d972d09
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180506"
---
# <a name="_com_errorwcodetohresult"></a>_com_error::WCodeToHRESULT

**Microsoft 专用**

将16位*wCode*映射到32位 HRESULT。

## <a name="syntax"></a>语法

```
static HRESULT WCodeToHRESULT(
   WORD wCode
) throw( );
```

#### <a name="parameters"></a>parameters

*wCode*<br/>
要映射到32位 HRESULT 的16位*wCode* 。

## <a name="return-value"></a>返回值

从16位*wCode*映射的32位 HRESULT。

## <a name="remarks"></a>备注

请参阅[WCode](../cpp/com-error-wcode.md)成员函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)<br/>
[_com_error 类](../cpp/com-error-class.md)
