---
title: _com_raise_error
ms.date: 11/04/2016
f1_keywords:
- _com_raise_error
helpviewer_keywords:
- _com_raise_error function
ms.assetid: a98226c2-c3fe-44f1-8ff5-85863de11cd6
ms.openlocfilehash: 5790fceef26d6de4edff604270cc7108f764aced
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399247"
---
# <a name="comraiseerror"></a>_com_raise_error

**Microsoft 专用**

将引发[_com_error](../cpp/com-error-class.md)中响应失败。

## <a name="syntax"></a>语法

```
void __stdcall _com_raise_error(
   HRESULT hr,
   IErrorInfo* perrinfo = 0
);
```

#### <a name="parameters"></a>参数

*hr*<br/>
HRESULT 的信息。

*perrinfo*<br/>
`IErrorInfo` 对象。

## <a name="remarks"></a>备注

**_com_raise_error**，其定义中\<comdef.h >，可由用户编写相同的名称和原型的版本替换。 若要使用 `#import` 但不使用 C++ 异常处理，则可以执行此操作。 在此情况下，用户版 **_com_raise_error**可能决定执行`longjmp`或显示一个消息框并暂停。 但不应返回用户版本，因为编译器 COM 支持代码不希望返回它。

此外可以使用[_set_com_error_handler](../cpp/set-com-error-handler.md)来替换默认错误处理函数。

默认情况下 **_com_raise_error**定义，如下所示：

```cpp
void __stdcall _com_raise_error(HRESULT hr, IErrorInfo* perrinfo) {
   throw _com_error(hr, perrinfo);
}
```

**结束 Microsoft 专用**

## <a name="requirements"></a>要求

**标头：** \<comdef.h >

**Lib:** 如果**wchar_t 是本机类型**编译器选项已打开，请使用 comsuppw.lib 或 comsuppwd.lib。 如果**wchar_t 是本机类型**未启用，请使用 comsupp.lib。 有关详细信息，请参阅 [/Zc:wchar_t（wchar_t 是本机类型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)。

## <a name="see-also"></a>请参阅

[编译器 COM 全局函数](../cpp/compiler-com-global-functions.md)<br/>
[_set_com_error_handler](../cpp/set-com-error-handler.md)