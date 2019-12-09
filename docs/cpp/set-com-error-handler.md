---
title: _set_com_error_handler
ms.date: 11/04/2016
helpviewer_keywords:
- _set_com_error_handler function
ms.assetid: 49fe4fca-5e37-4d83-abaf-15be5ce37f94
ms.openlocfilehash: 226dce24de68edd66ca68c43e41ce0cb5b8a1b48
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857289"
---
# <a name="_set_com_error_handler"></a>_set_com_error_handler

替换用于 COM 错误处理的默认函数。 **_set_com_error_handler**是 Microsoft 特定的。

## <a name="syntax"></a>语法

```
void __stdcall _set_com_error_handler(
   void (__stdcall *pHandler)(
      HRESULT hr,
      IErrorInfo* perrinfo
   )
);
```

#### <a name="parameters"></a>参数

*pHandler*<br/>
指向替换函数的指针。

*hr*<br/>
HRESULT 信息。

*perrinfo*<br/>
`IErrorInfo` 对象。

## <a name="remarks"></a>备注

默认情况下， [_com_raise_error](../cpp/com-raise-error.md)处理所有 com 错误。 你可以通过使用 **_set_com_error_handler**调用你自己的错误处理函数来更改此行为。

替换函数必须具有与 `_com_raise_error` 的签名等效的签名。

## <a name="example"></a>示例

```cpp
// _set_com_error_handler.cpp
// compile with /EHsc
#include <stdio.h>
#include <comdef.h>
#include <comutil.h>

// Importing ado dll to attempt to establish an ado connection.
// Not related to _set_com_error_handler
#import "C:\Program Files\Common Files\System\ado\msado15.dll" no_namespace rename("EOF", "adoEOF")

void __stdcall _My_com_raise_error(HRESULT hr, IErrorInfo* perrinfo)
{
   throw "Unable to establish the connection!";
}

int main()
{
   _set_com_error_handler(_My_com_raise_error);
   _bstr_t bstrEmpty(L"");
   _ConnectionPtr Connection = NULL;
   try
   {
      Connection.CreateInstance(__uuidof(Connection));
      Connection->Open(bstrEmpty, bstrEmpty, bstrEmpty, 0);
   }
   catch(char* errorMessage)
   {
      printf("Exception raised: %s\n", errorMessage);
   }

   return 0;
}
```

```Output
Exception raised: Unable to establish the connection!
```

## <a name="requirements"></a>需求

**标头：** \<comdef.h >

**Lib：** 如果指定了 **/zc： wchar_t**编译器选项（默认值），请使用 comsuppw.lib 或 comsuppwd.lib。 如果指定了 **/zc： wchar_t**编译器选项，请使用 comsupp.lib。 有关详细信息，包括如何在 IDE 中设置此选项，请参阅[/zc： wchar_t （Wchar_t 是本机类型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)。

## <a name="see-also"></a>另请参阅

[编译器 COM 全局函数](../cpp/compiler-com-global-functions.md)
