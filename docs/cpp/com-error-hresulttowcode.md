---
title: _com_error::HRESULTToWCode
ms.date: 11/04/2016
f1_keywords:
- _com_error::HRESULTToWCode
helpviewer_keywords:
- HRESULTToWCode method [C++]
ms.assetid: ff3789f5-1047-41a0-b7e3-86dd8f638dba
ms.openlocfilehash: 35a497c273f15c9755d3607e7907a3a48dad8dc8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180558"
---
# <a name="_com_errorhresulttowcode"></a>_com_error::HRESULTToWCode

**Microsoft 专用**

将32位 HRESULT 映射到16位 `wCode`。

## <a name="syntax"></a>语法

```
static WORD HRESULTToWCode(
   HRESULT hr
) throw( );
```

#### <a name="parameters"></a>parameters

*人事*<br/>
要映射到16位 `wCode`的32位 HRESULT。

## <a name="return-value"></a>返回值

从32位 HRESULT 映射16位 `wCode`。

## <a name="remarks"></a>备注

有关详细信息，请参阅[_com_error：： WCode](../cpp/com-error-wcode.md) 。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)<br/>
[_com_error 类](../cpp/com-error-class.md)
