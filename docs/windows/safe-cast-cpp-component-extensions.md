---
title: safe_cast （c + + 组件扩展） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- safe_cast
- safe_cast_cpp
- stdcli::language::safe_cast
dev_langs:
- C++
helpviewer_keywords:
- safe_cast keyword [C++]
ms.assetid: 4fa688bf-a8ec-49bc-a4c5-f48134efa4f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c889d39df4d900beba5c9b41015e62293fdbbcde
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891511"
---
# <a name="safecast-c-component-extensions"></a>safe_cast（C++ 组件扩展）
如果成功，则 `safe_cast` 操作以指定类型的形式返回指定表达式；否则引发 `InvalidCastException`。  
  
## <a name="all-runtimes"></a>所有运行时  
 （此语言功能没有适用于所有运行时的备注。）  
  
### <a name="syntax"></a>语法  
  
```cpp  
[default]:: safe_cast<  
type-id  
>(  
expression  
)  
  
```  
  
### <a name="parameters"></a>参数  
  
### <a name="remarks"></a>备注  
  
## <a name="windows-runtime"></a>Windows 运行时  
 `safe_cast` 允许你更改指定表达式的类型。 在完全可预期变量或参数会转换为特定类型的情况下，可以使用不带 try-catch 块的 safe_cast 在开发过程中检测编程错误。 有关详细信息，请参阅[强制转换 (C + + /cli CX)](http://msdn.microsoft.com/library/windows/apps/hh755802.aspx)。  
  
### <a name="syntax"></a>语法  
  
```cpp  
[default]:: safe_cast<  
type-id  
>(  
expression  
)  
  
```  
  
### <a name="parameters"></a>参数  
 *类型 id*  
 要转换的类型*表达式*到。 引用或值类型的句柄、值类型或是对引用或值类型的跟踪引用。  
  
 *表达式*  
 一个表达式，计算结果是引用或值类型的句柄、值类型或是对引用或值类型的跟踪引用。  
  
### <a name="remarks"></a>备注  
 `safe_cast` 引发`InvalidCastException`如果无法转换*表达式*到由指定的类型*类型 id*。若要捕获`InvalidCastException`，指定[/EH （异常处理模型）](../build/reference/eh-exception-handling-model.md)编译器选项，并使用 try/catch 语句。  
  
### <a name="requirements"></a>要求  
 编译器选项： **/ZW**  
  
### <a name="examples"></a>示例  
 **示例**  
  
 下面的代码示例演示如何使用`safe_cast`与 Windows 运行时。  
  
```cpp#  
// safe_cast_ZW.cpp  
// compile with: /ZW /EHsc  
  
using namespace default;  
using namespace Platform;  
  
interface class I1 {};  
interface class I2 {};  
interface class I3 {};  
  
ref class X : public I1, public I2 {};  
  
int main(Array<String^>^ args) {  
   I1^ i1 = ref new X;  
   I2^ i2 = safe_cast<I2^>(i1);   // OK, I1 and I2 have common type: X  
   // I2^ i3 = static_cast<I2^>(i1);   C2440 use safe_cast instead  
   try {  
      I3^ i4 = safe_cast<I3^>(i1);   // Fails because i1 is not derived from I3.  
   }   
   catch(InvalidCastException^ ic) {  
     wprintf(L"Caught expected exception: %s\n", ic->Message);  
   }  
}  
```  
  
 **输出**  
  
```Output  
Caught expected exception: InvalidCastException  
```  
  
## <a name="common-language-runtime"></a>公共语言运行时 
 `safe_cast` 允许更改表达式的类型并生成可验证的 MSIL 代码。  
  
### <a name="syntax"></a>语法  
  
```cpp  
[cli]:: safe_cast<  
type-id  
>(  
expression  
)  
  
```  
  
### <a name="parameters"></a>参数  
 *类型 id*  
 引用或值类型的句柄、值类型或是对引用或值类型的跟踪引用。  
  
 *表达式*  
 一个表达式，计算结果是引用或值类型的句柄、值类型或是对引用或值类型的跟踪引用。  
  
### <a name="remarks"></a>备注  
 表达式`safe_cast<`*类型 id*`>(`*表达式*`)`将操作数表达式转换为类型 type-id 的对象。  
  
 编译器将接受[static_cast](../cpp/static-cast-operator.md)在它将接受的大多数位置`safe_cast`。  但是，`safe_cast` 可保证生成可验证的 MSIL，而 `static_cast` 可能会生成无法验证的 MSIL。  请参阅[纯代码和可验证代码 (C + + /cli CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)和[Peverify.exe （PEVerify 工具）](/dotnet/framework/tools/peverify-exe-peverify-tool)有关详细信息可验证代码。  
  
 与 `static_cast` 一样，`safe_cast` 会调用用户定义的转换。  
  
 有关强制转换的详细信息，请参阅[强制转换运算符](../cpp/casting-operators.md)。  
  
 `safe_cast` 不适用于**const_cast** (丢掉**const**)。  
  
 `safe_cast` 位于 cli 命名空间中。  请参阅[平台、 default 和 cli 命名空间](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md)有关详细信息。  
  
 有关详细信息**safe_cas**t，请参阅：  
  
-   [/Clr 下的 C 样式强制转换 (C + + /cli CLI)](../windows/c-style-casts-with-clr-cpp-cli.md)  
  
-   [如何：在 C++/CLI 中使用 safe_cast](../dotnet/how-to-use-safe-cast-in-cpp-cli.md)  

### <a name="requirements"></a>要求  
 编译器选项： **/clr**  
  
### <a name="examples"></a>示例  
 **示例**  
  
 编译器不接受 `static_cast` 但接受 `safe_cast` 的情况的一个示例是不相关接口类型之间的强制转换。  使用 `safe_cast` 时，编译器不会发出转换错误，会在运行时执行检查以查看强转换是否可以进行  
  
```cpp  
// safe_cast.cpp  
// compile with: /clr  
using namespace System;  
  
interface class I1 {};  
interface class I2 {};  
interface class I3 {};  
  
ref class X : public I1, public I2 {};  
  
int main() {  
   I1^ i1 = gcnew X;  
   I2^ i2 = safe_cast<I2^>(i1);   // OK, I1 and I2 have common type: X  
   // I2^ i3 = static_cast<I2^>(i1);   C2440 use safe_cast instead  
   try {  
      I3^ i4 = safe_cast<I3^>(i1);   // fail at runtime, no common type  
   }   
   catch(InvalidCastException^) {  
      Console::WriteLine("Caught expected exception");  
   }  
}  
```  
  
 **输出**  
  
```Output  
Caught expected exception  
```  
  
## <a name="see-also"></a>请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)