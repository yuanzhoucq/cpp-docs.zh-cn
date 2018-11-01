---
title: ConvertStringToBSTR
ms.date: 11/04/2016
f1_keywords:
- ConvertStringToBSTR
helpviewer_keywords:
- ConvertStringToBSTR function
ms.assetid: 071f9b3b-9643-4e06-a1e5-de96ed15bab2
ms.openlocfilehash: 5e7d8abd29033fc88dae1e83fcc6467fb0ace46f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50485379"
---
# <a name="convertstringtobstr"></a>ConvertStringToBSTR

**Microsoft 专用**

将转换`char *`值设为`BSTR`。

## <a name="syntax"></a>语法

```
BSTR __stdcall ConvertStringToBSTR(const char* pSrc)
```

#### <a name="parameters"></a>参数

*pSrc*<br/>
一个`char *`变量。

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

**Lib:** comsuppw.lib 或 comsuppwd.lib (请参阅[/zc: wchar_t （wchar_t 是本机类型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)有关详细信息)

## <a name="see-also"></a>请参阅

[编译器 COM 全局函数](../cpp/compiler-com-global-functions.md)