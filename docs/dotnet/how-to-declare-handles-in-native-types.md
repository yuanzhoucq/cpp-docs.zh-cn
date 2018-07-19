---
title: 如何： 声明在本机类型中的句柄 |Microsoft 文档
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
f1_keywords:
- gcroot
dev_langs:
- C++
helpviewer_keywords:
- handles, declaring
- gcroot keyword [C++]
- types [C++], declaring handles in
ms.assetid: b8c0eead-17e5-4003-b21f-b673f997d79f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4573aac37eedecceab861eb41a70fc858b409fec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33130966"
---
# <a name="how-to-declare-handles-in-native-types"></a>如何：使用本机类型声明句柄
不能声明中本机类型的句柄类型。 vcclr.h 提供类型安全包装模板`gcroot`从 c + + 堆引用 CLR 对象。 此模板允许您在本机类型中嵌入虚拟句柄并将它视为它是基础类型。 在大多数情况下，你可以使用`gcroot`对象作为嵌入类型使用，而不需要任何转换。 但是，对于[对于每一个，在](../dotnet/for-each-in.md)，你必须使用`static_cast`来检索基础的托管的引用。  
  
 `gcroot`模板实现到已垃圾回收堆中使用的值类 System::Runtime::InteropServices::GCHandle，提供"句柄"功能。 请注意句柄本身不是垃圾回收并在不再使用时中的析构函数释放`gcroot`类 （此析构函数不能手动调用）。 如果实例化`gcroot`对象上本机堆中，必须调用删除对该资源。  
  
 运行时将维护句柄和它所引用的 CLR 对象之间的关联。 当 CLR 对象会随已垃圾回收堆一起移动时，句柄将返回对象的新地址。 变量没有被固定之前它将分配给`gcroot`模板。  
  
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
 此示例演示如何使用`gcroot`在本机类型中保存对值类型 （而不是引用类型） 的引用，使用`gcroot`上已装箱的类型。  
  
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