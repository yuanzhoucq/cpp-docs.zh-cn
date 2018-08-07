---
title: 枚举类 （c + + 组件扩展） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 8010fa8c-bad6-45b4-8214-b4db64d7ffe1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: af936151b221b11c88f6dd054779b1a74fa50571
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570543"
---
# <a name="enum-class--c-component-extensions"></a>枚举类（C++ 组件扩展）
在命名空间范围内声明枚举，该枚举是用户定义的类型，其包含称为枚举数的一组命名常数。  
  
## <a name="all-runtimes"></a>所有运行时  
 **备注**  
  
 C + + /CX 和 C + + /cli CLI 支持**公共枚举类**和**私有枚举类**哪些是类似于标准 c + +**枚举类**但添加了可访问性说明符。 下 **/clr**，C + + 11**枚举类**类型允许，但会生成警告 C4472，其目的是确保真正需要的是 ISO 枚举类型，而不是 C + + /CX 和 C + + /cli CLI 类型。 有关 ISO 标准 c + + 的详细信息**enum**关键字，请参阅[枚举](../cpp/enumerations-cpp.md)。  
  
## <a name="windows-runtime"></a>Windows 运行时  
 **语法**  
  
```  
      access  
      enum class  
      enumeration-identifier  
      [:underlying-type] { enumerator-list } [var];  
accessenum structenumeration-identifier[:underlying-type] { enumerator-list } [var];  
```  
  
 **参数**  
  
 *access*  
 可以是枚举的可访问性**公共**或**专用**。  
  
 *enumeration-identifier*  
 枚举的名称。  
  
 *underlying-type*  
 （可选）枚举的基础类型。  
  
 （可选。 Windows 仅限运行时） 的基础类型的枚举，它可以是**bool**， **char**， `char16`， `int16`， `uint16`， **int**， `uint32`， `int64`，或`uint64`。  
  
 *enumerator-list*  
 以逗号分隔的枚举器名称列表。  
  
 每个枚举数的值都是一个常数表达式，由编译器隐式定义或由表示法 *enumerator*`=`*constant-expression*。 如果隐式定义第一个枚举器，则其值为零。 每个后续的隐式定义的枚举器值是前一个枚举器的值 + 1。  
  
 *var*  
 （可选）枚举类型的变量的名称。  
  
 **备注**  
  
 有关详细信息和示例，请参阅 [枚举](http://msdn.microsoft.com/%20library/windows/apps/hh755820.aspx)。  
  
 请注意，如果可定义枚举器的值的常数表达式不能由 *underlying-type*表示，则编译器将发出错误消息。  但是，编译器不会报告不适用于基础类型的值的错误。 例如：  
  
-   如果 *underlying-type* 是数字，并且枚举器指定了该类型的最大值，则不会显示下一个隐式定义的枚举值。  
  
-   如果*基础类型*是**bool**，且两个以上的枚举器隐式定义后不能表示的前两个枚举器。  
  
-   如果 *underlying-type* 是 `char16`，且枚举值的范围是从 0xD800 到 0xDFFF，则可显示该值。 但是，该值出现逻辑错误，因为它表示半个 Unicode 代理项对，且不会以分隔形式显示。  
  
### <a name="requirements"></a>要求  
 编译器选项： **/ZW**  
  
## <a name="common-language-runtime"></a>公共语言运行时 
 **语法**  
  
```  
      access  
      enum class  
      name [:type] { enumerator-list } var;  
accessenum structname [:type] { enumerator-list } var;  
```  
  
 **参数**  
  
 *access*  
 枚举的可访问性。 可以是**公共**或**专用**。  
  
 *enumerator-list*  
 枚举中以逗号分隔的标识符（枚举器）列表。  
  
 *name*  
 枚举的名称。 不允许匿名托管枚举。  
  
 *类型*（可选）  
 *标识符*的基础类型。 这可以是任何标量类型，例如符号或无符号的版本**int**，**短**，或**长**。  **bool**或**char**还允许使用。  
  
 *var* （可选）  
 枚举类型的变量的名称。  
  
 **备注**  
  
 **enum class** 和 **enum struct** 是等效声明。  
  
 有两种枚举：托管或 C++/CX 枚举和标准枚举。  
  
 托管或 C++/CX 枚举可能有如下定义，  
  
```cpp  
public enum class day {sun, mon };  
```  
  
 并且在语义上等效于：  
  
```cpp  
ref class day {  
public:  
   static const int sun = 0;  
   static const int mon = 1;  
};  
```  
  
 标准枚举可能有如下定义：  
  
```cpp  
enum day2 { sun, mon };  
```  
  
 并且在语义上等效于：  
  
```cpp  
static const int sun = 0;  
static const int mon = 1;  
```  
  
 托管枚举器名称 (*identifiers*) 注入到定义枚举的作用域；必须完全限定对枚举器的所有引用 (*name*`::`*identifier*)。  为此，你不能定义匿名托管的枚举。  
  
 将标准枚举的枚举器强注入到封闭作用域。  即，如果存在名称与封闭作用域中的枚举器名称相同的另一个符号，则编译器将生成错误。  
  
 在 Visual C ++ 2002 和 Visual C ++ 2003 中，很有可能注入了枚举器（在封闭作用域中可见，除非具有相同名称的另一个标识符）。  
  
 如果定义了标准 c + + 枚举 (无需**类**或**结构**)，编译`/clr`将导致枚举编译为托管枚举。  枚举仍然具有非托管枚举的语义。  注意：编译器插入 Visual C++ 编译器可识别的属性 `Microsoft::VisualC::NativeEnumAttribute`，以标识程序员想将枚举变为本机枚举。  其他编译器只会将标准枚举视为托管枚举。  
  
 名为的与已编译的标准枚举`/clr`会显示在为托管枚举的程序集和可供任何其他托管编译器。   但是，未命名的标准枚举不会在程序集中公开可见。  
  
 在 Visual C ++ 2002 和 Visual C ++ 2003 中，用作函数参数中的类型的标准枚举：  
  
```cpp  
// mcppv2_enum.cpp  
// compile with: /clr  
enum E { a, b };  
void f(E) {System::Console::WriteLine("hi");}  
  
int main() {  
   E myi = b;  
   f(myi);  
}  
```  
  
 将发出 MSIL 形式的以下内容用于函数签名：  
  
```  
void f(int32);  
```  
  
 但是，在当前版本的编译器中，标准枚举将作为属性为 [NativeEnumAttribute] 的托管枚举以及采用 MSIL 形式的以下内容发出，以用于函数签名：  
  
```  
void f(E)  
```  
  
 有关本机枚举的更多信息，请参见 [C++ 枚举声明](../cpp/enumerations-cpp.md)。  
  
 有关 CLR 枚举的更多信息，请参阅：  
  
-   [枚举的基础类型。](../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md)  
  
### <a name="requirements"></a>要求  
 编译器选项： **/clr**  
  
### <a name="examples"></a>示例  
 **示例**  
  
 降序  
  
```cpp  
// mcppv2_enum_2.cpp  
// compile with: /clr  
// managed enum  
public enum class m { a, b };  
  
// standard enum  
public enum n { c, d };  
  
// unnamed, standard enum  
public enum { e, f } o;  
  
int main()   
{  
   // consume managed enum  
   m mym = m::b;  
   System::Console::WriteLine("no automatic conversion to int: {0}", mym);  
   System::Console::WriteLine("convert to int: {0}", (int)mym);  
  
   // consume standard enum  
   n myn = d;  
   System::Console::WriteLine(myn);  
  
   // consume standard, unnamed enum  
   o = f;  
   System::Console::WriteLine(o);  
}   
```  
  
 **输出**  
  
```Output  
no automatic conversion to int: b  
  
convert to int: 1  
  
1  
  
1  
```  
  
## <a name="see-also"></a>请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)