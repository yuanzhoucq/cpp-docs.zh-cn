---
title: ConvertStringToBSTR
ms.date: 11/04/2016
f1_keywords:
- ConvertStringToBSTR
helpviewer_keywords:
- ConvertStringToBSTR function
ms.assetid: 071f9b3b-9643-4e06-a1e5-de96ed15bab2
ms.openlocfilehash: 2065011ee6bbf98ce2c83be494f1e6631af9f7cf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170704"
---
# <a name="convertstringtobstr"></a>ConvertStringToBSTR

**Microsoft 专用**

将 `char *` 值转换为 `BSTR`。

## <a name="syntax"></a>语法

```
BSTR __stdcall ConvertStringToBSTR(const char* pSrc)
```

#### <a name="parameters"></a>parameters

*.Psrc*<br/>
一个 `char *` 变量。

## <a name="example"></a>示例

```cpp
// ConvertStringToBSTR.cpp
#include <comutil.h>
#include <stdio.h>

#pragma comment(lib, "comsuppw.lib")
#pragma comment(lib, "kernel32.lib")

int main() {
   char* lpszText = "Test";
   printf_s("char * text: %s\n", lpszText);

   BSTR bstrText = _com_util::ConvertStringToBSTR(lpszText);
   wprintf_s(L"BSTR text: %s\n", bstrText);

   SysFreeString(bstrText);
}
```

```Output
char * text: Test
BSTR text: Test
```

**结束 Microsoft 专用**

## <a name="requirements"></a>要求

**标头：** \<comutil.h >

**Lib：** comsuppw.lib 或 comsuppwd.lib （有关详细信息，请参阅[/zc： Wchar_t （Wchar_t 为本机类型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)

## <a name="see-also"></a>另请参阅

[编译器 COM 全局函数](../cpp/compiler-com-global-functions.md)
