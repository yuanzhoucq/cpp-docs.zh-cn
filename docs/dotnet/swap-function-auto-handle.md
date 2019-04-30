---
title: swap 函数 (auto_handle)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msclr::swap
- msclr.swap
helpviewer_keywords:
- swap function
ms.assetid: 7dd91b5c-f0de-4634-a2e2-642626706e27
ms.openlocfilehash: eb410d420e91f9b64742d74d9f9262a4db42f562
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384551"
---
# <a name="swap-function-autohandle"></a>swap 函数 (auto_handle)

交换对象之间一个`auto_handle`和另一个。

## <a name="syntax"></a>语法

```
template<typename _element_type>
void swap(
   auto_handle<_element_type> % _left,
   auto_handle<_element_type> % _right
);
```

#### <a name="parameters"></a>参数

*_left*<br/>
一个 `auto_handle`。

*_right*<br/>
另一个`auto_handle`。

## <a name="example"></a>示例

```
// msl_swap_auto_handle.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

using namespace System;
using namespace msclr;

int main() {
   auto_handle<String> s1 = "string one";
   auto_handle<String> s2 = "string two";

   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",
      s1->ToString(), s2->ToString() );
   swap( s1, s2 );
   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",
      s1->ToString(), s2->ToString() );
}
```

```Output
s1 = 'string one', s2 = 'string two'
s1 = 'string two', s2 = 'string one'
```

## <a name="requirements"></a>要求

**标头文件** \<msclr\auto_handle.h >

**Namespace** msclr

## <a name="see-also"></a>请参阅

[auto_handle](../dotnet/auto-handle.md)<br/>
[auto_handle::swap](../dotnet/auto-handle-swap.md)
