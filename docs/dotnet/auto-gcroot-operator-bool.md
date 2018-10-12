---
title: auto_gcroot::operator bool |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- auto_gcroot.operator bool
- auto_gcroot::operator bool
- msclr.auto_gcroot.operator bool
- msclr::auto_gcroot::operator bool
- operator bool
dev_langs:
- C++
helpviewer_keywords:
- bool operator
ms.assetid: 87d38498-4221-4de8-8d02-c2dd2e6274ec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c2fe517809db7cecacc7a0190e0dae94ef55c35d
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161185"
---
# <a name="autogcrootoperator-bool"></a>auto_gcroot::operator bool

使用运算符`auto_gcroot`条件表达式中。

## <a name="syntax"></a>语法

```
operator bool() const;
```

## <a name="return-value"></a>返回值

**true**已包装的对象是否有效，则为**false**否则为。

## <a name="remarks"></a>备注

此运算符实际将转换为`_detail_class::_safe_bool`这是比更安全**bool**因为不能将它转换为整型类型。

## <a name="example"></a>示例

```cpp
// msl_auto_gcroot_operator_bool.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

int main() {
   auto_gcroot<String^> s;
   if ( s ) Console::WriteLine( "s is valid" );
   if ( !s ) Console::WriteLine( "s is invalid" );
   s = "something";
   if ( s ) Console::WriteLine( "now s is valid" );
   if ( !s ) Console::WriteLine( "now s is invalid" );
   s.reset();
   if ( s ) Console::WriteLine( "now s is valid" );
   if ( !s ) Console::WriteLine( "now s is invalid" );
}
```

```Output
s is invalid
now s is valid
now s is invalid
```

## <a name="requirements"></a>要求

**标头文件** \<msclr\auto_gcroot.h >

**Namespace** msclr

## <a name="see-also"></a>请参阅

[auto_gcroot 成员](../dotnet/auto-gcroot-members.md)<br/>
[auto_gcroot::operator!](../dotnet/auto-gcroot-operator-logical-not.md)