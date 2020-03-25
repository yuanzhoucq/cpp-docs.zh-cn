---
title: _com_raise_error
ms.date: 11/04/2016
f1_keywords:
- _com_raise_error
helpviewer_keywords:
- _com_raise_error function
ms.assetid: a98226c2-c3fe-44f1-8ff5-85863de11cd6
ms.openlocfilehash: 2012ec98d8d40d60a7f12feb68bdc371e1616223
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189788"
---
# <a name="_com_raise_error"></a>_com_raise_error

**Microsoft 专用**

引发[_com_error](../cpp/com-error-class.md)以响应失败。

## <a name="syntax"></a>语法

```
void __stdcall _com_raise_error(
   HRESULT hr,
   IErrorInfo* perrinfo = 0
);
```

#### <a name="parameters"></a>parameters

*人事*<br/>
HRESULT 信息。

*perrinfo*<br/>
`IErrorInfo` 对象。

## <a name="remarks"></a>备注

**_com_raise_error**（在 \<comdef.h > 中定义）可以替换为同一名称和原型的用户编写版本。 若要使用 `#import` 但不使用 C++ 异常处理，则可以执行此操作。 在这种情况下，用户版本的 **_com_raise_error**可能决定执行 `longjmp` 或显示消息框并停止操作。 但不应返回用户版本，因为编译器 COM 支持代码不希望返回它。

你还可以使用[_set_com_error_handler](../cpp/set-com-error-handler.md)来替换默认的错误处理函数。

默认情况下，按如下所示定义 **_com_raise_error** ：

```cpp
void __stdcall _com_raise_error(HRESULT hr, IErrorInfo* perrinfo) {
   throw _com_error(hr, perrinfo);
}
```

**结束 Microsoft 专用**

## <a name="requirements"></a>要求

**标头：** \<comdef.h >

**Lib：** 如果**wchar_t 是本机类型**编译器选项，请使用 comsuppw.lib 或 comsuppwd.lib。 如果**wchar_t 为 "本机" 类型**为 "关"，请使用 comsupp.lib。 有关详细信息，请参阅 [/Zc:wchar_t（wchar_t 是本机类型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)。

## <a name="see-also"></a>另请参阅

[编译器 COM 全局函数](../cpp/compiler-com-global-functions.md)<br/>
[_set_com_error_handler](../cpp/set-com-error-handler.md)
