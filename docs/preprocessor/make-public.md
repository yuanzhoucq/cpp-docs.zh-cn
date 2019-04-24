---
title: make_public
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.make_public
- make_public_CPP
helpviewer_keywords:
- pragmas, make_public
- make_public pragma
ms.assetid: c3665f4d-268a-4932-9661-c37c8ae6a341
ms.openlocfilehash: d569758f90b9e55f65ad13517f86dea41d151ca8
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039119"
---
# <a name="makepublic"></a>make_public
指示本机类型应具有公共程序集可访问性。

## <a name="syntax"></a>语法

```
#pragma make_public(type)
```

### <a name="parameters"></a>参数

*类型*是想要具有公共程序集可访问性的类型的名称。

## <a name="remarks"></a>备注

**make_public**对于想要引用的本机类型时不能更改的.h 文件很有用。 若要在带有公共程序集可见性的类型中使用公共函数签名中的本机类型，则本机类型还必须具有公共程序集可访问性，否则编译器将发出警告。

**make_public**必须在全局范围内指定，并且它仅在从点影响它的位置声明到源代码文件的末尾。

本机类型可能是隐式或显式私有;请参阅[类型的可见性](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility)有关详细信息。

## <a name="examples"></a>示例

以下示例是包含两个本机结构的定义的 .h 文件的内容。

```cpp
// make_public_pragma.h
struct Native_Struct_1 { int i; };
struct Native_Struct_2 { int i; };
```

下面的代码示例使用标头文件，并表明除非你显式标记为公共的将本机结构使用，否则**make_public**，当您尝试使用本机结构中的时，编译器会生成一个警告中的公共托管类型的公共函数的签名。

```cpp
// make_public_pragma.cpp
// compile with: /c /clr /W1
#pragma warning (default : 4692)
#include "make_public_pragma.h"
#pragma make_public(Native_Struct_1)

public ref struct A {
   void Test(Native_Struct_1 u) {u.i = 0;}   // OK
   void Test(Native_Struct_2 u) {u.i = 0;}   // C4692
};
```

## <a name="see-also"></a>请参阅

[Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)