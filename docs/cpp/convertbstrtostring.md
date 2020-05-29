---
title: ConvertBSTRToString
ms.date: 11/04/2016
f1_keywords:
- ConvertBSTRToString
helpviewer_keywords:
- ConvertBSTRToString function
ms.assetid: ab6ce555-3d75-4e9c-9cb8-ada6d8ce43b1
ms.openlocfilehash: 1d0ad8727dd4d5ec06a45ec26c67dd3ad268f524
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189516"
---
# <a name="convertbstrtostring"></a>ConvertBSTRToString

**Microsoft 专用**

将 `BSTR` 值转换为 `char *`。

## <a name="syntax"></a>语法

```
char* __stdcall ConvertBSTRToString(BSTR pSrc);
```

#### <a name="parameters"></a>parameters

*.Psrc*<br/>
BSTR 变量。

## <a name="remarks"></a>备注

**ConvertBSTRToString**分配必须删除的字符串。

## <a name="example"></a>示例

```cpp
// ConvertBSTRToString.cpp
#include <comutil.h>
#include <stdio.h>

#pragma comment(lib, "comsuppw.lib")

int main() {
   BSTR bstrText = ::SysAllocString(L"Test");
   wprintf_s(L"BSTR text: %s\n", bstrText);

   char* lpszText2 = _com_util::ConvertBSTRToString(bstrText);
   printf_s("char * text: %s\n", lpszText2);

   SysFreeString(bstrText);
   delete[] lpszText2;
}
```

```Output
BSTR text: Test
char * text: Test
```

**结束 Microsoft 专用**

## <a name="requirements"></a>要求

**标头：** \<comutil.h >

**Lib：** comsuppw.lib 或 comsuppwd.lib （有关详细信息，请参阅[/zc： Wchar_t （Wchar_t 为本机类型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)

## <a name="see-also"></a>另请参阅

[编译器 COM 全局函数](../cpp/compiler-com-global-functions.md)
