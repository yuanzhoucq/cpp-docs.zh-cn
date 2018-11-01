---
title: _com_error::HRESULTToWCode
ms.date: 11/04/2016
f1_keywords:
- _com_error::HRESULTToWCode
helpviewer_keywords:
- HRESULTToWCode method [C++]
ms.assetid: ff3789f5-1047-41a0-b7e3-86dd8f638dba
ms.openlocfilehash: d89503e822d92bf6a1fcb2b6bb658d532af32c5d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581228"
---
# <a name="comerrorhresulttowcode"></a>_com_error::HRESULTToWCode

**Microsoft 专用**

将 32 位 HRESULT 映射到 16 位`wCode`。

## <a name="syntax"></a>语法

```
static WORD HRESULTToWCode(
   HRESULT hr
) throw( );
```

#### <a name="parameters"></a>参数

*hr*<br/>
若要映射到 16 位的 32 位 HRESULT `wCode`。

## <a name="return-value"></a>返回值

16 位`wCode`从 32 位 HRESULT 映射。

## <a name="remarks"></a>备注

请参阅[_com_error:: wcode](../cpp/com-error-wcode.md)有关详细信息。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)<br/>
[_com_error 类](../cpp/com-error-class.md)