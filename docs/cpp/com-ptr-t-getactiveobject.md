---
title: _com_ptr_t::GetActiveObject
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::GetActiveObject
helpviewer_keywords:
- GetActiveObject method [C++]
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
ms.openlocfilehash: 84e43de9c40baa3c596c68ed7739471c059cbac7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484495"
---
# <a name="comptrtgetactiveobject"></a>_com_ptr_t::GetActiveObject

**Microsoft 专用**

将附加到给定的对象的现有实例`CLSID`或`ProgID`。

## <a name="syntax"></a>语法

```
HRESULT GetActiveObject(
   const CLSID& rclsid
) throw( );
HRESULT GetActiveObject(
   LPCWSTR clsidString
) throw( );
HRESULT GetActiveObject(
   LPCSTR clsidStringA
) throw( );
```

#### <a name="parameters"></a>参数

*rclsid*<br/>
`CLSID`的对象。

*clsidString*<br/>
由 Unicode 字符串，包含`CLSID`(从"**{**") 或`ProgID`。

*clsidStringA*<br/>
使用 ANSI 代码页，包含的多字节字符串`CLSID`(从"**{**") 或`ProgID`。

## <a name="remarks"></a>备注

这些成员函数调用**GetActiveObject**来检索指向已向 OLE 注册的正在运行对象的指针，然后查询此智能指针的接口类型。 生成的指针随后将封装在此 `_com_ptr_t` 对象内。 `Release` 调用以减少前面封装指针的引用计数。 此例程将返回 HRESULT，指示成功或失败。

- **GetActiveObject (**`rclsid`**)** 将附加到给定的对象的现有实例`CLSID`。

- **GetActiveObject (**`clsidString`**)** 附加到给定的 Unicode 字符串，包含对象的现有实例`CLSID`(从"**{**") 或`ProgID`.

- **GetActiveObject (**`clsidStringA`**)** 附加到给定的多字节字符字符串，包含对象的现有实例`CLSID`(从"**{**") 或`ProgID`. 调用[MultiByteToWideChar](/windows/desktop/api/stringapiset/nf-stringapiset-multibytetowidechar)，其假定该字符串为中的 ANSI 代码页而不是 OEM 代码页。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_com_ptr_t 类](../cpp/com-ptr-t-class.md)