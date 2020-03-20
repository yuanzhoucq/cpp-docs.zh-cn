---
title: 如何：使用本机类型声明句柄
ms.custom: get-started-article
ms.date: 11/04/2016
f1_keywords:
- gcroot
helpviewer_keywords:
- handles, declaring
- gcroot keyword [C++]
- types [C++], declaring handles in
ms.assetid: b8c0eead-17e5-4003-b21f-b673f997d79f
ms.openlocfilehash: 11dbc196a89a224afe02312fbe4dff99d8467f4c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545035"
---
# <a name="how-to-declare-handles-in-native-types"></a>如何：使用本机类型声明句柄

不能在本机类型中声明句柄类型。 vcclr 提供了类型安全的包装器模板 `gcroot` 从C++堆中引用 CLR 对象。 此模板允许您在本机类型中嵌入虚拟句柄，并将其视为基础类型。 在大多数情况下，可以使用 `gcroot` 对象作为嵌入类型，而无需任何强制转换。 但是，[对于每个，在中](../dotnet/for-each-in.md)，你必须使用 `static_cast` 来检索基础托管引用。

使用值类 System：： Runtime：： InteropServices：： GCHandle 的功能实现 `gcroot` 模板，后者向垃圾回收堆提供 "handles"。 请注意，句柄本身不会被垃圾回收，并且会在 `gcroot` 类中的析构函数不再使用时将其释放（不能手动调用此析构函数）。 如果在本机堆上实例化 `gcroot` 对象，则必须对该资源调用 delete。

运行时将维护句柄与它所引用的 CLR 对象之间的关联。 当 CLR 对象与垃圾回收堆一起移动时，句柄将返回对象的新地址。 不需要先固定变量，然后才能将其分配给 `gcroot` 的模板。

## <a name="example"></a>示例

此示例演示如何在本机堆栈上创建 `gcroot` 对象。

```cpp
// mcpp_gcroot.cpp
// compile with: /clr
#include <vcclr.h>
using namespace System;

class CppClass {
public:
   gcroot<String^> str;   // can use str as if it were String^
   CppClass() {}
};

int main() {
   CppClass c;
   c.str = gcnew String("hello");
   Console::WriteLine( c.str );   // no cast required
}
```

```Output
hello
```

## <a name="example"></a>示例

此示例演示如何在本机堆上创建 `gcroot` 对象。

```cpp
// mcpp_gcroot_2.cpp
// compile with: /clr
// compile with: /clr
#include <vcclr.h>
using namespace System;

struct CppClass {
   gcroot<String ^> * str;
   CppClass() : str(new gcroot<String ^>) {}

   ~CppClass() { delete str; }

};

int main() {
   CppClass c;
   *c.str = gcnew String("hello");
   Console::WriteLine( *c.str );
}
```

```Output
hello
```

## <a name="example"></a>示例

此示例演示如何通过对装箱类型使用 `gcroot`，使用 `gcroot` 在本机类型中保存对值类型的引用（而不是引用类型）。

```cpp
// mcpp_gcroot_3.cpp
// compile with: /clr
#include < vcclr.h >
using namespace System;

public value struct V {
   String^ str;
};

class Native {
public:
   gcroot< V^ > v_handle;
};

int main() {
   Native native;
   V v;
   native.v_handle = v;
   native.v_handle->str = "Hello";
   Console::WriteLine("String in V: {0}", native.v_handle->str);
}
```

```Output
String in V: Hello
```

## <a name="see-also"></a>另请参阅

[使用 C++ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)
