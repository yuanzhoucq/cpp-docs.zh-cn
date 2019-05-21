---
title: 上下文相关关键字（C++/CLI 和 C++/CX）
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- internal_CPP
helpviewer_keywords:
- context-sensitive keywords
ms.assetid: e33da089-f434-44e9-8cce-4668d05a8939
ms.openlocfilehash: ca289a7ebd4578d5c67bb5d3e403d2a9a2756520
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516122"
---
# <a name="context-sensitive-keywords--ccli-and-ccx"></a>上下文相关关键字（C++/CLI 和 C++/CX）

上下文相关关键字是仅在特定上下文中才能识别出来的语言元素。 在特定的上下文以外，区分上下文关键字可以是用户定义的符号。

## <a name="all-runtimes"></a>所有运行时

### <a name="remarks"></a>备注

下面是区上下文关键字的列表：

- [abstract](abstract-cpp-component-extensions.md)

- [delegate](delegate-cpp-component-extensions.md)

- [event](event-cpp-component-extensions.md)

- [finally](../dotnet/finally.md)

- [for each, in](../dotnet/for-each-in.md)

- [initonly](../dotnet/initonly-cpp-cli.md)

- `internal`

- [名称](literal-cpp-component-extensions.md)

- [override](override-cpp-component-extensions.md)

- [属性](property-cpp-component-extensions.md)

- [sealed](sealed-cpp-component-extensions.md)

- `where`（属于[泛型](generics-cpp-component-extensions.md)）

出于可读性目的，建议限制为仅将上下文相关关键字用作用户定义符号。

## <a name="windows-runtime"></a>Windows 运行时

### <a name="remarks"></a>备注

（此功能没有特定于平台的备注。）

### <a name="requirements"></a>要求

编译器选项：`/ZW`

## <a name="common-language-runtime"></a>公共语言运行时

### <a name="remarks"></a>备注

（此功能没有特定于平台的备注。）

### <a name="requirements"></a>要求

编译器选项：`/clr`

### <a name="examples"></a>示例

下面的代码示例展示了在相应上下文中，property 上下文相关关键字可用于定义属性和变量。

```cpp
// context_sensitive_keywords.cpp
// compile with: /clr
public ref class C {
   int MyInt;
public:
   C() : MyInt(99) {}

   property int Property_Block {   // context-sensitive keyword
      int get() { return MyInt; }
   }
};

int main() {
   int property = 0;               // variable name
   C ^ MyC = gcnew C();
   property = MyC->Property_Block;
   System::Console::WriteLine(++property);
}
```

```Output
100
```

## <a name="see-also"></a>请参阅

[ .NET 和 UWP 的组件扩展](component-extensions-for-runtime-platforms.md)