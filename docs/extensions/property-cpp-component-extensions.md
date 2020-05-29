---
title: property（C++/CLI 和 C++/CX）
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- property keyword [C++]
ms.assetid: cc79d2b2-f013-4d81-8252-eece97a18704
ms.openlocfilehash: b961a93628752b11cd1d147268a4947acf29f67a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171971"
---
# <a name="property--ccli-and-ccx"></a>property（C++/CLI 和 C++/CX）

声明属性，这是行为和访问方式与数据成员或数组元素类似的成员函数。

## <a name="all-runtimes"></a>所有运行时

你可以声明以下一种属性类型。

简单属性<br/>
默认创建分配属性值的 set 取值函数、检索属性值的 get 取值函数，以及编译器生成的私有数据成员（其中包含属性值）。

属性块<br/>
用于创建用户定义的 get 和/或 set 访问器。 如果定义了 get 及 set 访问器，则属性为读/写，如果只定义了 get 访问器，则属性为只读，如果只定义了 set 访问器，则属性为只写。

必须显式声明数据成员，以包含属性值。

索引属性<br/>
可用于获取和设置由一个或多个索引指定的属性值的属性块。

可以创建包含用户定义属性名或默认属性名的索引属性。 默认索引属性的名称是在其中定义该属性的类的名称。 若要声明默认属性，请指定 default 关键字，而不是属性名。

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

### <a name="parameters"></a>parameters

type<br/>
属性值的数据类型，因此是属性本身。

property_name<br/>
属性的名称。

access-modifier<br/>
访问限定符。 有效限定符为 static 和 virtual。

get 或 set 取值函数无需就 virtual 限定符达成一致，但必须就 static 限定符达成一致。

inheritance-modifier<br/>
继承限定符。 有效限定符为 abstract 和 sealed。

index_list<br/>
以逗号分隔的一个或多个索引列表。 每个索引包含索引类型，以及可以在属性方法体中使用的可选标识符。

*value*<br/>
在设置操作中分配给属性的值，或在 get 操作中检索的值。

property_body<br/>
Set 或 get 访问器的属性方法体。 property_body 可以使用 index_list 来访问基础属性数据成员，或在用户定义处理中将它用作参数。

## <a name="windows-runtime"></a>Windows 运行时

有关详细信息，请参阅[属性 (C++/CX)](../cppcx/properties-c-cx.md)。

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

### <a name="parameters"></a>parameters

modifier<br/>
可用于属性声明或 get/set 访问器方法的修饰符。 可取值为 static 和 virtual。

type<br/>
由属性表示的值类型。

property_name<br/>
引发方法的参数；必须与委托签名匹配。

index_list<br/>
一个或多个以逗号分隔的索引的列表，在方括号（下标运算符 ([])）中指定。 对于每个索引，指定类型以及选择指定可以在属性方法体中使用的标识符。

### <a name="remarks"></a>备注

第一个语法示例展示了同时隐式声明 *和* 方法的简单属性`set``get`。 编译器将自动创建私有字段以存储属性值。

第二个语法示例展示了同时显式声明 *和* 方法的属性块`set``get`。

第三个语法示例展示了客户定义的索引属性。 除了要设置或检索的值外，索引属性也接受参数。 必须指定属性名。 与简单的属性不同，索引属性的 `set` 和/或 `get` 方法必须显式定义，并且必须指定属性名。

第四个语法示例展示了提供对类型实例的类似数组访问权限的默认属性。 关键字 default 仅用于指定默认属性。 默认属性的名称是定义属性所属类型的名称。

property 关键字可以出现在类、接口或值类型中。 属性可以有 get 函数（只读）、set 函数（只写）或二者皆可（读写）。

属性名不能匹配包含它的托管类的名称。 getter 函数的返回类型必须与相应的 setter 函数的最后一个参数的类型匹配。

对于客户端代码，属性具有普通数据成员的外观，并可以通过使用与数据成员相同的语法进行写入或读取。

get 和 set 方法无需就 virtual 修饰符达成一致。

Get 和 set 方法的可访问性可能有所不同。

属性方法的定义可以出现类主体外部，就像普通方法一样。

属性的 get 和 set 方法应就 static 修饰符达成一致。

如果属性的 get 和 set 方法适合以下说明，则为标量：

- Get 方法没有参数，并且具有 `T` 返回类型。

- set 方法有类型为 `T` 的参数，并返回类型 void。

具有相同标识符的作用域中应只声明一个标量属性。 不能重载标量属性。

声明属性数据成员时，编译器将数据成员（有时称为“后备存储”）插入类中。 但是，数据成员名称具有一定的形式，你无法引用源中的成员，就像是包含类的实际数据成员一样。 使用 ildasm.exe 查看类型的元数据，并查看属性后备存储区的编译器生成的名称。

属性块中的访问器方法允许不同的访问性。  也就是说，set 方法可以是公共的，而 get 方法可以是私有的。  但是，访问器方法的限制可访问性比属性本身的声明上所述的更弱是错误的。

property 是上下文相关关键字。  有关详细信息，请参阅[上下文相关关键字](context-sensitive-keywords-cpp-component-extensions.md)。

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

```Output
test

21
```

## <a name="see-also"></a>另请参阅

[ .NET 和 UWP 的组件扩展](component-extensions-for-runtime-platforms.md)
