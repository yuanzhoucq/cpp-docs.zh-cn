---
title: 属性参数类型 （c + + 组件扩展） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- custom attributes, parameter types
ms.assetid: d9f127a3-7f08-456f-acc6-256805632712
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 84c97dc0eb449ed0a2e835c46e77981dda0b67e2
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611901"
---
# <a name="attribute-parameter-types--c-component-extensions"></a>特性参数类型（C++ 组件扩展）

编译器在编译时必须知道传递给特性的值。  特性参数可为下列类型：

- **bool**

- **char**， **unsigned char**

- short、unsigned short

- **int**，**无符号的整数**

- **长**，**无符号长**

- **__int64**， **unsigned 的 __int64**

- **float**，**双精度**

- **wchar_t**

- `char*` 或 `wchar_t*` 或 `System::String*`

- `System::Type ^`

- `System::Object ^`

- **enum**

## <a name="example"></a>示例

### <a name="code"></a>代码

```cpp
// attribute_parameter_types.cpp
// compile with: /clr /c
using namespace System;
ref struct AStruct {};

[AttributeUsage(AttributeTargets::ReturnValue)]
ref struct Attr : public Attribute {
   Attr(AStruct ^ i){}
   Attr(bool i){}
   Attr(){}
};

ref struct MyStruct {
   static AStruct ^ x = gcnew AStruct;
   [returnvalue:Attr(x)] int Test() { return 0; }   // C3104
   [returnvalue:Attr] int Test2() { return 0; }   // OK
   [returnvalue:Attr(true)] int Test3() { return 0; }   // OK
};
```

## <a name="example"></a>示例

### <a name="description"></a>描述

当指定特性时，所有未命名（位置）的参数必须优先于命名参数。

### <a name="code"></a>代码

```cpp
// extending_metadata_c.cpp
// compile with: /clr /c
using namespace System;
[AttributeUsage(AttributeTargets::Class)]
ref class MyAttr : public Attribute {
public:
   MyAttr() {}
   MyAttr(int i) {}
   property int Priority;
   property int Version;
};

[MyAttr]
ref class ClassA {};   // No arguments

[MyAttr(Priority = 1)]
ref class ClassB {};   // Named argument

[MyAttr(123)]
ref class ClassC {};   // Positional argument

[MyAttr(123, Version = 1)]
ref class ClassD {};   // Positional and named
```

## <a name="example"></a>示例

### <a name="description"></a>描述

特性参数可以为上述类型的一维数组。

### <a name="code"></a>代码

```cpp
// extending_metadata_d.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::Class)]
public ref struct ABC : public Attribute {
   ABC(array<int>^){}
   array<double> ^ param;
};

[ABC( gcnew array<int> {1,2,3}, param = gcnew array<double>{2.71, 3.14})]
ref struct AStruct{};
```

## <a name="see-also"></a>请参阅

[用户定义的特性](../windows/user-defined-attributes-cpp-component-extensions.md)