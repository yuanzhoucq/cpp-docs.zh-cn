---
title: 如何：本机类型声明句柄
ms.custom: get-started-article
ms.date: 11/04/2016
f1_keywords:
- gcroot
helpviewer_keywords:
- handles, declaring
- gcroot keyword [C++]
- types [C++], declaring handles in
ms.assetid: b8c0eead-17e5-4003-b21f-b673f997d79f
ms.openlocfilehash: f5d6d31be9f3c10e1a56639ccf20663ce59d7941
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57745978"
---
# <a name="how-to-declare-handles-in-native-types"></a>如何：本机类型声明句柄

不能声明中的本机类型的句柄类型。 vcclr.h 提供类型安全的包装器模板`gcroot`从 c + + 堆引用 CLR 对象。 此模板允许您在本机类型中嵌入虚拟句柄，并将它视为像它是一样的基础类型。 在大多数情况下，可以使用`gcroot`作为嵌入类型而不需要任何转换的对象。 但是，对于[对于每个，在](../dotnet/for-each-in.md)，你必须使用`static_cast`来检索基本托管的引用。

`gcroot`到垃圾回收堆使用的值类 System::Runtime::InteropServices::GCHandle，提供"handles"功能实现的模板。 请注意，句柄本身不是垃圾回收并在不再使用时中的析构函数释放`gcroot`类 （此析构函数不能手动调用）。 如果实例化`gcroot`本机堆上对象必须调用删除对该资源。

在运行时将保持该句柄和它所引用的 CLR 对象之间的关联。 当 CLR 对象移动与垃圾回收堆时，该句柄将返回该对象的新地址。 不需要固定之前分配给一个变量`gcroot`模板。

## <a name="example"></a>示例

此示例演示如何创建`gcroot`本机堆栈上的对象。

```
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

此示例演示如何创建`gcroot`本机堆上的对象。

```
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

此示例演示如何使用`gcroot`若要在本机类型中保存对值类型 （而不是引用类型） 的引用，使用`gcroot`上已装箱的类型。

```
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

## <a name="see-also"></a>请参阅

[使用 C++ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)
