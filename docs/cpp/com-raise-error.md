---
title: _com_raise_error
ms.date: 11/04/2016
f1_keywords:
- _com_raise_error
helpviewer_keywords:
- _com_raise_error function
ms.assetid: a98226c2-c3fe-44f1-8ff5-85863de11cd6
ms.openlocfilehash: f5efbe98a489a380c4e9be5a0e40603be2a409c0
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745082"
---
# <a name="_com_raise_error"></a>_com_raise_error

**微软特定**

引发[_com_error](../cpp/com-error-class.md)以响应故障。

## <a name="syntax"></a>语法

```cpp
void __stdcall _com_raise_error(
   HRESULT hr,
   IErrorInfo* perrinfo = 0
);
```

#### <a name="parameters"></a>参数

*人力资源*<br/>
HRESULT 信息。

*佩里info*<br/>
`IErrorInfo` 对象。

## <a name="remarks"></a>备注

**_com_raise_error（** 在 comdef.h>中\<定义）可以替换为同名和原型的用户编写的版本。 若要使用 `#import` 但不使用 C++ 异常处理，则可以执行此操作。 在这种情况下 **，_com_raise_error**的用户版本可能会决定执行 或`longjmp`显示消息框并停止。 但不应返回用户版本，因为编译器 COM 支持代码不希望返回它。

您还可以使用[_set_com_error_handler](../cpp/set-com-error-handler.md)来替换默认的错误处理函数。

默认情况下 **，_com_raise_error**的定义如下：

```cpp
void __stdcall _com_raise_error(HRESULT hr, IErrorInfo* perrinfo) {
   throw _com_error(hr, perrinfo);
}
```

**结束微软特定**

## <a name="requirements"></a>要求

**标题：** \<comdef.h>

**Lib：** 如果**wchar_t是本机类型**编译器选项，请使用 comsuppw.lib 或 comsuppwd.lib。 如果**wchar_t是本机类型**关闭，请使用 comsupp.lib。 有关详细信息，请参阅 [/Zc:wchar_t（wchar_t 是本机类型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)。

## <a name="see-also"></a>请参阅

[编译器 COM 全局函数](../cpp/compiler-com-global-functions.md)<br/>
[_set_com_error_handler](../cpp/set-com-error-handler.md)
