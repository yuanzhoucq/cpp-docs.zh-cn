---
title: override（C++/CLI 和 C++/CX）
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- overriding, override keyword [C++]
- override keyword [C++]
ms.assetid: 34d19257-1686-4fcd-96f5-af07c70ba914
ms.openlocfilehash: 8dc7a0a0e6cf759d956fd701d033bd773e572af3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515652"
---
# <a name="override--ccli-and-ccx"></a>override（C++/CLI 和 C++/CX）

override 上下文相关关键字指明，类型成员重写基类或基接口成员。

## <a name="remarks"></a>备注

在为本机目标（默认编译器选项）、Windows 运行时目标（`/ZW` 编译器选项）或公共语言运行时目标（`/clr` 编译器选项）编译时，override 关键字有效。

若要详细了解重写说明符，请参阅[重写说明符](../cpp/override-specifier.md)和[重写说明符和本机编译](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)。

若要详细了解上下文相关关键字，请参阅[上下文相关关键字](context-sensitive-keywords-cpp-component-extensions.md)。

## <a name="examples"></a>示例

下面的代码示例展示了 override 还可以用于本机编译。

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

下面的代码示例展示了 override 可用于 Windows 运行时编译。

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

下面的代码示例展示了 override 可用于公共语言运行时编译。

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

[override 说明符](../cpp/override-specifier.md)<br/>
[重写说明符](override-specifiers-cpp-component-extensions.md)