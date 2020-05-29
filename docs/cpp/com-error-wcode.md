---
title: _com_error::WCode
ms.date: 11/04/2016
f1_keywords:
- _com_error::WCode
helpviewer_keywords:
- WCode method [C++]
ms.assetid: f3b21852-f8ea-4e43-bff1-11c2d35454c4
ms.openlocfilehash: 92dffbdbe034ef55be04c1b7d204be6880d8d4b2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190191"
---
# <a name="_com_errorwcode"></a>_com_error::WCode

**Microsoft 专用**

检索映射到封装的 HRESULT 中的16位错误代码。

## <a name="syntax"></a>语法

```
WORD WCode ( ) const throw( );
```

## <a name="return-value"></a>返回值

如果 HRESULT 在0x80040200 到0x8004FFFF 范围内，则 `WCode` 方法返回 HRESULT 减 0x80040200;否则，它返回零。

## <a name="remarks"></a>备注

`WCode` 方法用于撤消 COM 支持代码中发生的映射。 `dispinterface` 的属性或方法的包装器调用一个支持例程，该例程将参数打包并调用 `IDispatch::Invoke`。 返回时，如果返回 `DISP_E_EXCEPTION` 的失败 HRESULT，则从传递给 `IDispatch::Invoke`的 `EXCEPINFO` 结构检索错误信息。 错误代码可以是存储在 `EXCEPINFO` 结构的 `wCode` 成员中的16位值，也可以是 `EXCEPINFO` 结构的 `scode` 成员的完整32位值。 如果返回了16位 `wCode`，则必须先将其映射到32位的失败 HRESULT。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)<br/>
[_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)<br/>
[_com_error 类](../cpp/com-error-class.md)
