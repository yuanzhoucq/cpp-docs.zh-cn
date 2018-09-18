---
title: '_com_error:: wcode |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::WCode
dev_langs:
- C++
helpviewer_keywords:
- WCode method [C++]
ms.assetid: f3b21852-f8ea-4e43-bff1-11c2d35454c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: da4ad7d7f06c9cb6ae1a75a4c17cc63b377a9845
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036509"
---
# <a name="comerrorwcode"></a>_com_error::WCode

**Microsoft 专用**

检索映射到封装 HRESULT 的 16 位错误代码。

## <a name="syntax"></a>语法

```
WORD WCode ( ) const throw( );
```

## <a name="return-value"></a>返回值

如果 HRESULT 范围 0x80040200 到 0x8004FFFF 内`WCode`方法将返回的 HRESULT 减去 0x80040200; 否则，它将返回零。

## <a name="remarks"></a>备注

`WCode`方法用于撤消发生在 COM 支持代码中的映射。 包装器`dispinterface`属性或方法调用的参数和调用包的支持例程`IDispatch::Invoke`。 在返回时，如果失败的 HRESULT 的`DISP_E_EXCEPTION`返回，则从检索错误信息`EXCEPINFO`结构传递给`IDispatch::Invoke`。 错误代码可以是存储在一个 16 位值`wCode`的成员`EXCEPINFO`结构或中的全 32 位值`scode`的成员`EXCEPINFO`结构。 如果 16 位`wCode`返回，则必须首先将映射到 32 位失败 HRESULT。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)<br/>
[_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)<br/>
[_com_error 类](../cpp/com-error-class.md)