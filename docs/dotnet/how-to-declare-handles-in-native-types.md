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
ms.openlocfilehash: 1aca21402122a0c8641a7e57ace2a3477ff96f01
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221336"
---
# <a name="how-to-declare-handles-in-native-types"></a>如何：使用本机类型声明句柄

不能在本机类型中声明句柄类型。 vcclr 提供了类型安全的包装器模板 `gcroot` ，用于引用 c + + 堆中的 CLR 对象。 此模板允许您在本机类型中嵌入虚拟句柄，并将其视为基础类型。 在大多数情况下，你可以将 `gcroot` 对象用作嵌入类型，而无需任何强制转换。 但是，[对于每个，在中](../dotnet/for-each-in.md)，你必须使用 **`static_cast`** 来检索基础托管引用。

该 `gcroot` 模板是使用值类 System：： Runtime：： InteropServices：： GCHandle 的工具实现的，后者向垃圾回收堆提供 "句柄"。 请注意，句柄本身不会被垃圾回收，并且会在类中的析构函数不再使用时释放 `gcroot` （不能手动调用此析构函数）。 如果在 `gcroot` 本机堆上实例化对象，则必须对该资源调用 delete。

运行时将维护句柄与它所引用的 CLR 对象之间的关联。 当 CLR 对象与垃圾回收堆一起移动时，句柄将返回对象的新地址。 在将变量分配给模板之前，无需将其固定 `gcroot` 。

## <a name="example"></a>示例

此示例演示如何 `gcroot` 在本机堆栈上创建对象。

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

此示例演示如何 `gcroot` 在本机堆上创建对象。

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

此示例演示如何使用 `gcroot` `gcroot` 在装箱类型上保存对本机类型中的值类型（而不是引用类型）的引用。

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

[使用 c + + 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)
