---
title: _com_ptr_t::CreateInstance
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::CreateInstance
helpviewer_keywords:
- CreateInstance method [C++]
ms.assetid: ab89b0e1-9da3-4784-a079-58b17340f111
ms.openlocfilehash: 82b180b3f40683495ed2cfa284bdae8e1afaef9e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498652"
---
# <a name="_com_ptr_tcreateinstance"></a>_com_ptr_t::CreateInstance

**Microsoft 专用**

在`CLSID`给定或`ProgID`的情况创建对象的新实例。

## <a name="syntax"></a>语法

```
HRESULT CreateInstance(
   const CLSID& rclsid,
   IUnknown* pOuter=NULL,
   DWORD dwClsContext = CLSCTX_ALL
) throw( );
HRESULT CreateInstance(
   LPCWSTR clsidString,
   IUnknown* pOuter=NULL,
   DWORD dwClsContext = CLSCTX_ALL
) throw( );
HRESULT CreateInstance(
   LPCSTR clsidStringA,
   IUnknown* pOuter=NULL,
   DWORD dwClsContext = CLSCTX_ALL
) throw( );
```

#### <a name="parameters"></a>参数

*rclsid*<br/>
`CLSID`对象的。

*clsidString*<br/>
包含`CLSID` (以 " **{** " 开头) 或的`ProgID`Unicode 字符串。

*clsidStringA*<br/>
使用 ANSI 代码页的多字节字符串, 其中包含一个`CLSID` (以 " **{** `ProgID`" 开头) 或。

*dwClsContext*<br/>
运行可执行代码的上下文。

*pOuter*<br/>
[聚合](../atl/aggregation.md)的外部未知。

## <a name="remarks"></a>备注

这些成员函数调用 `CoCreateInstance` 来创建新的 COM 对象，然后查询此智能指针的接口类型。 生成的指针随后将封装在此 `_com_ptr_t` 对象内。 `Release`调用以减小先前封装的指针的引用计数。 此例程返回 HRESULT 以指示成功或失败。

- **CreateInstance (** *rclsid* **，** *dwClsContext* **)** 创建给定的对象的新运行实例`CLSID`.

- **CreateInstance (** *clsidString* **，** *dwClsContext* **)** 创建给定的对象的新运行实例Unicode 字符串包含`CLSID`(从" **{** ") 或`ProgID`。

- **CreateInstance (** *clsidStringA* **，** *dwClsContext* **)** 创建给定的对象的新运行实例多字节字符字符串包含`CLSID`(从" **{** ") 或`ProgID`。 调用[MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar), 它假定字符串位于 ANSI 代码页而非 OEM 代码页中。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_com_ptr_t 类](../cpp/com-ptr-t-class.md)