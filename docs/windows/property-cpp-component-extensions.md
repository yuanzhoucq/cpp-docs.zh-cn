---
title: 属性 （c + + 组件扩展） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- property_cpp
- property
dev_langs:
- C++
helpviewer_keywords:
- property keyword [C++]
ms.assetid: cc79d2b2-f013-4d81-8252-eece97a18704
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5fbf0b3c9db19e839d6832415cfd8ed6eb9b93a2
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39604113"
---
# <a name="property--c-component-extensions"></a>属性（C++ 组件扩展）
声明*属性*，它是一个成员函数，其行为和访问数据成员或数组元素等。  
  
## <a name="all-runtimes"></a>所有运行时  
 你可以声明以下一种属性类型。  
  
 *简单的属性*  
 默认情况下，会创建*set 访问器*分配的属性值， *get 访问器*检索属性值，并包含属性值的编译器生成的私有数据成员。  
  
 *属性块*  
 用于创建用户定义的 get 和/或 set 访问器。 如果定义了 get 及 set 访问器，则属性为读/写，如果只定义了 get 访问器，则属性为只读，如果只定义了 set 访问器，则属性为只写。  
  
 必须显式声明数据成员，以包含属性值。  
  
 *索引的属性*  
 可用于获取和设置由一个或多个索引指定的属性值的属性块。  
  
 可以创建索引的属性，其具有用户定义的属性名称或*默认*属性名称。 默认索引属性的名称是在其中定义该属性的类的名称。 若要声明默认属性，指定**默认**关键字而不是属性名称。  
  
 必须显式声明数据成员，以包含属性值。 对于索引属性，数据成员通常是一个数组或集合。  
  
### <a name="syntax"></a>语法  
  
```cpp  
property type property_name;

property type property_name { 
   access-modifier type get() inheritance-modifier {property_body}; 
   access-modifier void set(type value) inheritance-modifier {property_body};
} 

property type property_name[index_list] { 
   access-modifier type get(index_list) inheritance-modifier {property_body}; 
   access-modifier void set(index_list, value) inheritance-modifier {property_body};
} 

property type default[index_list] { 
   access-modifier type get(index_list) inheritance-modifier {property_body};
   access-modifier void set(index_list, value) inheritance-modifier {property_body};
}  
```  
  
### <a name="parameters"></a>参数  
 *type*  
 属性值的数据类型，因此是属性本身。  
  
 *property_name*  
 属性的名称。  
  
 *访问修饰符*  
 访问限定符。 是有效的限定符**静态**并**虚拟**。  
  
 Get 或 set 访问器不需要能达成**虚拟**限定符，但它们必须达成**静态**限定符。  
  
 *继承修饰符*  
 继承限定符。 是有效的限定符**抽象**并**密封**。  
  
 *index_list*  
 以逗号分隔的一个或多个索引列表。 每个索引包含索引类型，以及可以在属性方法体中使用的可选标识符。  
  
 *value*  
 在设置操作中分配给属性的值，或在 get 操作中检索的值。  
  
 *property_body*  
 Set 或 get 访问器的属性方法体。 *Property_body*可以使用*index_list*访问基础属性数据成员，或作为用户定义的处理中的参数。  
  
## <a name="windows-runtime"></a>Windows 运行时  
 有关详细信息，请参阅[属性 (C + + /cli CX)](http://msdn.microsoft.com/library/windows/apps/hh755807.aspx)。  
  
### <a name="requirements"></a>要求  
 编译器选项：`/ZW`  
  
## <a name="common-language-runtime"></a>公共语言运行时 
### <a name="syntax"></a>语法  
  
```cpp  
modifier property type property_name;

modifier property type property_name {
   modifier void set(type);
   modifier type get();
}
modifier property type property_name[index-list, value] {
   modifier void set(index-list, value);
   modifier type get(index-list);

modifier property type default[index];
}  
```  
  
### <a name="parameters"></a>参数  
  
 *修饰符*  
 可用于属性声明或 get/set 访问器方法的修饰符。 可能的值为**静态**并**虚拟**。  
  
 *type*  
 由属性表示的值类型。  
  
 *property_name*  
 引发方法的参数；必须与委托签名匹配。  
  
 *index_list*  
 一个或多个以逗号分隔的索引的列表，在方括号（下标运算符 ([])）中指定。 对于每个索引，指定类型以及选择指定可以在属性方法体中使用的标识符。  
  
### <a name="remarks"></a>备注  
  
 第一个语法示例所示*简单的属性*，其中同时隐式声明`set`和`get`方法。 编译器将自动创建私有字段以存储属性值。  
  
 第二个语法示例显示*属性块*，它同时显示声明`set`和`get`方法。  
  
 第三个语法示例显示了客户定义*属性编制索引*。 除了要设置或检索的值外，索引属性也接受参数。 必须指定属性名。 与简单的属性不同，索引属性的 `set` 和/或 `get` 方法必须显式定义，并且必须指定属性名。  
  
 第四个语法示例显示*默认*属性，它提供对类型的实例的类似数组的访问权限。 关键字**默认**，仅用于指定默认属性。 默认属性的名称是定义属性所属类型的名称。  
  
 **属性**关键字可以出现在类、 接口或值类型。 属性可以有 get 函数（只读）、set 函数（只写）或二者皆可（读写）。  
  
 属性名不能匹配包含它的托管类的名称。 getter 函数的返回类型必须与相应的 setter 函数的最后一个参数的类型匹配。  
  
 对于客户端代码，属性具有普通数据成员的外观，并可以通过使用与数据成员相同的语法进行写入或读取。  
  
 Get 和 set 方法不需要能达成**虚拟**修饰符。  
  
 Get 和 set 方法的可访问性可能有所不同。  
  
 属性方法的定义可以出现类主体外部，就像普通方法一样。  
  
 Get 和 set 方法的属性应达成**静态**修饰符。  
  
 如果属性的 get 和 set 方法适合以下说明，则为标量：  
  
-   Get 方法没有参数，并且具有 `T` 返回类型。  
  
-   Set 方法具有类型参数的`T`，并返回类型**void**。  
  
 具有相同标识符的作用域中应只声明一个标量属性。 不能重载标量属性。  
  
 声明属性数据成员时，编译器将数据成员（有时称为“后备存储”）插入类中。 但是，数据成员名称具有一定的形式，你无法引用源中的成员，就像是包含类的实际数据成员一样。 使用 ildasm.exe 查看类型的元数据，并查看属性后备存储区的编译器生成的名称。  
  
 属性块中的访问器方法允许不同的访问性。  也就是说，set 方法可以是公共的，而 get 方法可以是私有的。  但是，访问器方法的限制可访问性比属性本身的声明上所述的更弱是错误的。  
  
 **属性**是上下文相关关键字。  有关详细信息，请参阅[上下文相关的关键字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。  
  
  
### <a name="requirements"></a>要求  
 编译器选项：`/clr`  
  
### <a name="examples"></a>示例  
 以下示例演示声明和属性数据成员与属性块的使用。  它还显示可以从类定义的属性访问器。  
  
```cpp  
// mcppv2_property.cpp  
// compile with: /clr  
using namespace System;  
public ref class C {  
   int MyInt;  
public:  
  
   // property data member  
   property String ^ Simple_Property;  
  
   // property block  
   property int Property_Block {  
  
      int get();  
  
      void set(int value) {  
         MyInt = value;  
      }  
   }  
};  
  
int C::Property_Block::get() {  
   return MyInt;  
}  
  
int main() {  
   C ^ MyC = gcnew C();  
   MyC->Simple_Property = "test";  
   Console::WriteLine(MyC->Simple_Property);  
  
   MyC->Property_Block = 21;  
   Console::WriteLine(MyC->Property_Block);  
}  
```  
  
 **输出**  
  
```Output  
test  
  
21  
```  
  
## <a name="see-also"></a>请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)