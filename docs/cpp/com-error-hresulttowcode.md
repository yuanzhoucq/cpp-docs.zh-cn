---
title: _com_error::HRESULTToWCode |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::HRESULTToWCode
dev_langs:
- C++
helpviewer_keywords:
- HRESULTToWCode method [C++]
ms.assetid: ff3789f5-1047-41a0-b7e3-86dd8f638dba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c39b638451aa8ea89191e323eae5f2c140563990
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082061"
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