---
title: _com_ptr_t::GetActiveObject
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::GetActiveObject
helpviewer_keywords:
- GetActiveObject method [C++]
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
ms.openlocfilehash: ea8059a039b77811dd54d4a4937ad746b7ca0937
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170796"
---
# <a name="_com_ptr_tgetactiveobject"></a>_com_ptr_t::GetActiveObject

**Microsoft 专用**

如果给定 `CLSID` 或 `ProgID`，则附加到对象的现有实例。

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

#### <a name="parameters"></a>parameters

*rclsid*<br/>
对象的 `CLSID`。

*clsidString*<br/>
保留 `CLSID` （以 " **{** " 开头）或 `ProgID`的 Unicode 字符串。

*clsidStringA*<br/>
使用 ANSI 代码页的多字节字符串，其中包含一个 `CLSID` （以 " **{** " 开头）或 `ProgID`。

## <a name="remarks"></a>备注

这些成员函数调用**GetActiveObject**来检索指向已向 OLE 注册的正在运行的对象的指针，然后查询此智能指针的接口类型。 生成的指针随后将封装在此 `_com_ptr_t` 对象内。 调用 `Release` 来减小以前封装的指针的引用计数。 此例程返回 HRESULT 以指示成功或失败。

- **GetActiveObject （** `rclsid` **）** 在给定 `CLSID`的情况附加到对象的现有实例。

- **GetActiveObject （** `clsidString` **）** 在给定 Unicode `CLSID` 字符串（以 " **{** " 开头）或 `ProgID`的情况上，附加到对象的现有实例。

- **GetActiveObject （** `clsidStringA` **）** 根据给定的多字节字符 `CLSID` 字符串（以 " **{** " 开头）或 `ProgID`，附加到对象的现有实例。 调用[MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar)，它假定字符串位于 ANSI 代码页而非 OEM 代码页中。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[_com_ptr_t 类](../cpp/com-ptr-t-class.md)
