---
title: 上下文相关的关键字 (C + + /cli 和 C + + /cli CX) |Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal_CPP
dev_langs:
- C++
helpviewer_keywords:
- context-sensitive keywords
ms.assetid: e33da089-f434-44e9-8cce-4668d05a8939
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5d02939e61da4a247b46da5637c38d01e7990c49
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2018
ms.locfileid: "49327929"
---
# <a name="context-sensitive-keywords--ccli-and-ccx"></a>上下文相关的关键字 (C + + /cli 和 C + + /cli CX)

*上下文相关的关键字*是仅在特定上下文中识别的语言元素。 在特定的上下文以外，区分上下文关键字可以是用户定义的符号。

## <a name="all-runtimes"></a>所有运行时

### <a name="remarks"></a>备注

下面是区上下文关键字的列表：

- [abstract](../windows/abstract-cpp-component-extensions.md)

- [delegate](../windows/delegate-cpp-component-extensions.md)

- [event](../windows/event-cpp-component-extensions.md)

- [finally](../dotnet/finally.md)

- [for each, in](../dotnet/for-each-in.md)

- [initonly](../dotnet/initonly-cpp-cli.md)

- `internal`

- [名称](../windows/literal-cpp-component-extensions.md)

- [override](../windows/override-cpp-component-extensions.md)

- [属性](../windows/property-cpp-component-extensions.md)

- [sealed](../windows/sealed-cpp-component-extensions.md)

- `where` (属于[泛型](../windows/generics-cpp-component-extensions.md))

出于可读性目的，你可能想要限制区分上下文关键字作为用户定义的符号的使用。

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

下面的代码示例演示在适当的上下文中，**属性**上下文相关关键字可用于定义属性和变量。

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

[适用于.NET 和 UWP 组件扩展](../windows/component-extensions-for-runtime-platforms.md)