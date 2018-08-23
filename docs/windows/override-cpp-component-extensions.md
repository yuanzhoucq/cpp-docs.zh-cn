---
title: 重写 （c + + 组件扩展） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- overriding, override keyword [C++]
- override keyword [C++]
ms.assetid: 34d19257-1686-4fcd-96f5-af07c70ba914
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 708b69bc63e59d8ba6ba882d894d6f17b59d8237
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592364"
---
# <a name="override--c-component-extensions"></a>重写（C++ 组件扩展）

**重写**上下文相关关键字表示一种类型的成员重写基类或基接口成员。

## <a name="remarks"></a>备注

**重写**编译为本机目标 （默认编译器选项） 时，关键字是有效 Windows 运行时目标 (`/ZW`编译器选项)，或公共语言运行时目标 (`/clr`编译器选项)。

有关重写说明符的详细信息，请参阅[重写说明符](../cpp/override-specifier.md)并[重写说明符和本机编译](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)。

有关上下文相关关键字的详细信息，请参阅[上下文相关的关键字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。

## <a name="examples"></a>示例

下面的代码示例演示**重写**还可以在本机编译中使用。

```cpp
// override_keyword_1.cpp
// compile with: /c
struct I1 {
   virtual void f();
};

struct X : public I1 {
   virtual void f() override {}
};
```

### <a name="example"></a>示例

下面的代码示例演示**重写**可以在 Windows 运行时编译中使用。

```cpp 
// override_keyword_2.cpp
// compile with: /ZW /c
ref struct I1 {
   virtual void f();
};

ref struct X : public I1 {
   virtual void f() override {}
};
```

#### <a name="requirements"></a>要求

编译器选项：`/ZW`

### <a name="example"></a>示例

下面的代码示例演示**重写**可以在公共语言运行时编译中使用。

```cpp
// override_keyword_3.cpp
// compile with: /clr /c
ref struct I1 {
   virtual void f();
};

ref struct X : public I1 {
   virtual void f() override {}
};
```

#### <a name="requirements"></a>要求

编译器选项：`/clr`

## <a name="see-also"></a>请参阅

[override 说明符](../cpp/override-specifier.md)  
[重写说明符](../windows/override-specifiers-cpp-component-extensions.md)