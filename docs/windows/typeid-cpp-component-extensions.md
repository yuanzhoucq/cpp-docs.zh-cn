---
title: typeid （c + + 组件扩展） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- typeid keyword [C++]
ms.assetid: e9706cae-e7c4-4d6d-b474-646d73df3e70
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: db1efac0a38aaa11238452e418277f78dbcd6d9d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33888362"
---
# <a name="typeid--c-component-extensions"></a>typeid（C++ 组件扩展）
获取一个值，该值指示对象的类型。  
  
> [!WARNING]
>  本主题引用 typeid 的 C++ 组件扩展版本。 此关键字的 ISO c + + 版本，请参阅[typeid 运算符](../cpp/typeid-operator.md)。  
  
## <a name="all-runtimes"></a>所有运行时  
  
### <a name="syntax"></a>语法  
  
```cpp  
T::typeid  
```  
  
### <a name="parameters"></a>参数  
 *T*  
 类型名称。  
  
## <a name="windows-runtime"></a>Windows 运行时  
  
### <a name="syntax"></a>语法  
  
```cpp  
Platform::Type^ type = T::typeid;  
```  
  
### <a name="parameters"></a>参数  
 `T`  
 类型名称。  
  
### <a name="remarks"></a>备注  
 在 C + + /CX 中，typeid 返回[platform:: type](../cppcx/platform-type-class.md)构造中的运行时类型信息。  
  
### <a name="requirements"></a>要求  
 编译器选项： **/ZW**  
  
## <a name="common-language-runtime"></a>公共语言运行时 
 **语法**  
  
```  
  
type::typeid  
```  
  
 **参数**  
  
 *type*  
 你想要为其 system:: type 对象的类型 （抽象声明符） 的名称。  
  
 **备注**  
  
 `typeid` 用于获取<xref:System.Type>在编译时类型。  
  
 `typeid` 类似于在运行的时使用的类型获取 system:: type<xref:System.Type.GetType%2A>或<xref:System.Object.GetType%2A>。 但是，typeid 仅接受类型名称作为参数。  如果你想要使用一种类型的实例以获取其 system:: type 名称，使用 GetType。  
  
 `typeid` 必须能够在编译时，计算类型名称 （类型） 而 GetType 计算要在运行时返回的类型。  
  
 `typeid` 可能需要本机类型名称或公共语言运行时的本机类型名称; 别名请参阅[到 c + + 本机类型的.NET Framework 等效项 (C + + /cli CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)有关详细信息。  
  
 `typeid` 也适用于本机类型，尽管它仍将返回 system:: type。  若要获取 type_info 结构，请使用[typeid 运算符](../cpp/typeid-operator.md)。  
  
### <a name="requirements"></a>要求  
 编译器选项： **/clr**  
  
### <a name="examples"></a>示例  
 **示例**  
  
 下面的示例比较 GetType() 成员 typeid 关键字。  
  
```  
// keyword__typeid.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct G {  
   int i;  
};  
  
int main() {  
   G ^ pG = gcnew G;  
   Type ^ pType = pG->GetType();  
   Type ^ pType2 = G::typeid;  
  
   if (pType == pType2)  
      Console::WriteLine("typeid and GetType returned the same System::Type");  
   Console::WriteLine(G::typeid);  
  
   typedef float* FloatPtr;  
   Console::WriteLine(FloatPtr::typeid);  
}  
```  
  
 **输出**  
  
```Output  
typeid and GetType returned the same System::Type  
G  
  
System.Single*  
  
```  
  
 **示例**  
  
 下面的示例显示 system:: type 可以用于获取特性的类型的类型的变量。  它还演示，对于某些类型，你将必须创建要使用的 typedef `typeid`。  
  
```  
// keyword__typeid_2.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Security;  
using namespace System::Security::Permissions;  
  
typedef int ^ handle_to_int;  
typedef int * pointer_to_int;  
  
public ref class MyClass {};  
  
class MyClass2 {};  
  
[attribute(AttributeTargets::All)]  
ref class AtClass {  
public:  
   AtClass(Type ^) {  
      Console::WriteLine("in AtClass Type ^ constructor");  
   }  
};  
  
[attribute(AttributeTargets::All)]  
ref class AtClass2 {  
public:  
   AtClass2() {  
      Console::WriteLine("in AtClass2 constructor");  
   }  
};  
  
// Apply the AtClass and AtClass2 attributes to class B  
[AtClass(MyClass::typeid), AtClass2]     
[AttributeUsage(AttributeTargets::All)]  
ref class B : Attribute {};  
  
int main() {  
   Type ^ MyType = B::typeid;  
  
   Console::WriteLine(MyType->IsClass);  
  
   array<Object^>^ MyArray = MyType -> GetCustomAttributes(true);  
   for (int i = 0 ; i < MyArray->Length ; i++ )  
      Console::WriteLine(MyArray[i]);  
  
   if (int::typeid != pointer_to_int::typeid)  
      Console::WriteLine("int::typeid != pointer_to_int::typeid, as expected");  
  
   if (int::typeid == handle_to_int::typeid)  
      Console::WriteLine("int::typeid == handle_to_int::typeid, as expected");  
}  
```  
  
 **输出**  
  
```Output  
True  
  
in AtClass2 constructor  
  
in AtClass Type ^ constructor  
  
AtClass2  
  
System.AttributeUsageAttribute  
  
AtClass  
  
int::typeid != pointer_to_int::typeid, as expected  
  
int::typeid == handle_to_int::typeid, as expected  
```  
  
## <a name="see-also"></a>请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)