---
title: bitand
ms.date: 11/04/2016
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- std::bitand
- std.bitand
- bitand
helpviewer_keywords:
- bitand function
ms.assetid: 279cf9b5-fac1-49de-b329-f1a31b3481fe
ms.openlocfilehash: dabe6add3e0fd2711b9149d4fdad88a8dad4871a
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51517756"
---
# <a name="bitand"></a>bitand

& 运算符的替代项。

## <a name="syntax"></a>语法

```C

#define bitand &
```

## <a name="remarks"></a>备注

该宏产生运算符

## <a name="example"></a>示例

```cpp
// iso646_bitand.cpp
// compile with: /EHsc
#include <iostream>
#include <iso646.h>

int main( )
{
   using namespace std;
   int a = 1, b = 2, result;

   result = a & b;
   cout << result << endl;

   result= a bitand b;
   cout << result << endl;
}
```

```Output
0
0
```

## <a name="requirements"></a>要求

**标头：** \<iso646.h>