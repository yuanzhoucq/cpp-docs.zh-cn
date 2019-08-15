---
title: _com_ptr_t::GetActiveObject
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::GetActiveObject
helpviewer_keywords:
- GetActiveObject method [C++]
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
ms.openlocfilehash: f13a42878392f63096cdfcb405f3f91cc0efe451
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498893"
---
# <a name="_com_ptr_tgetactiveobject"></a>_com_ptr_t::GetActiveObject

**Microsoft 专用**

附加到给定`CLSID`或`ProgID`的对象的现有实例。

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
`CLSID`对象的。

*clsidString*<br/>
包含`CLSID` (以 " **{** " 开头) 或的`ProgID`Unicode 字符串。

*clsidStringA*<br/>
使用 ANSI 代码页的多字节字符串, 其中包含一个`CLSID` (以 " **{** `ProgID`" 开头) 或。

## <a name="remarks"></a>备注

这些成员函数调用**GetActiveObject**来检索指向已向 OLE 注册的正在运行的对象的指针, 然后查询此智能指针的接口类型。 生成的指针随后将封装在此 `_com_ptr_t` 对象内。 `Release`调用以减小先前封装的指针的引用计数。 此例程返回 HRESULT 以指示成功或失败。

- **GetActiveObject (** `rclsid` **)** 附加到给定的`CLSID`对象的现有实例。

- `clsidString`如果`CLSID`给定了包含 (以 " **{** " 开头) 或的`ProgID`Unicode 字符串, 则 GetActiveObject ( **)** 会附加到对象的现有实例。

- `clsidStringA`如果给定的多字节字符字符串`CLSID`包含一个 (以 " **{** " `ProgID`开头) 或, 则 GetActiveObject ( **)** 会附加到对象的现有实例。 调用[MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar), 它假定字符串位于 ANSI 代码页而非 OEM 代码页中。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_com_ptr_t 类](../cpp/com-ptr-t-class.md)