---
title: class (C++)
ms.date: 11/04/2016
f1_keywords:
- class_cpp
helpviewer_keywords:
- class types [C++], class statements
- class keyword [C++]
ms.assetid: dd23c09f-6598-4069-8bff-69c7f2518b9f
ms.openlocfilehash: 6475bc3703ce1bd7cf6103f4be8c12edc36e98b9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226003"
---
# <a name="class-c"></a>class (C++)

**`class`** 关键字声明类类型或定义类类型的对象。

## <a name="syntax"></a>语法

```
[template-spec]
class [ms-decl-spec] [tag [: base-list ]]
{
   member-list
} [declarators];
[ class ] tag declarators;
```

#### <a name="parameters"></a>参数

*template-规范*<br/>
可选模板规范。 有关详细信息，请参阅[模板](templates-cpp.md)。

class<br/>
**`class`** 关键字。

*decl-规范*<br/>
可选存储类规范。 有关详细信息，请参阅[__declspec](../cpp/declspec.md)关键字。

*标记*<br/>
赋予类的类型名称。 标记在类的范围内变成保留字。 标记是可选项。 如果省略，则定义匿名类。 有关详细信息，请参阅[匿名类类型](../cpp/anonymous-class-types.md)。

base-list**<br/>
此类将从中派生其成员的类或结构的可选列表。 有关详细信息，请参阅[基类](../cpp/base-classes.md)。 每个基类或结构名称的前面都可以是访问说明符（[public](../cpp/public-cpp.md)、 [private](../cpp/private-cpp.md)、 [protected](../cpp/protected-cpp.md)）和[virtual](../cpp/virtual-cpp.md)关键字。 有关详细信息，请参阅[控制对类成员的访问](member-access-control-cpp.md)中的成员访问表。

*成员列表*<br/>
类成员的列表。 有关详细信息，请参阅[类成员概述](../cpp/class-member-overview.md)。

*声明符*<br/>
指定类类型的一个或多个实例的名称的声明符列表。 如果类的所有数据成员都为，则声明符可以包含初始值设定项列表 **`public`** 。 这在结构中更为常见，它们的数据成员 **`public`** 默认情况下与类中的不同。 有关详细信息，请参阅[声明符的概述](../cpp/overview-of-declarators.md)。

## <a name="remarks"></a>备注

有关一般类的详细信息，请参阅以下主题之一：

- [struct](../cpp/struct-cpp.md)

- [union](../cpp/unions.md)

- [__multiple_inheritance](../cpp/inheritance-keywords.md)

- [__single_inheritance](../cpp/inheritance-keywords.md)

- [__virtual_inheritance](../cpp/inheritance-keywords.md)

有关 c + +/CLI 和 c + +/CX 中的托管类和结构的信息，请参阅[类和结构](../extensions/classes-and-structs-cpp-component-extensions.md)

## <a name="example"></a>示例

```cpp
// class.cpp
// compile with: /EHsc
// Example of the class keyword
// Exhibits polymorphism/virtual functions.

#include <iostream>
#include <string>
using namespace std;

class dog
{
public:
   dog()
   {
      _legs = 4;
      _bark = true;
   }

   void setDogSize(string dogSize)
   {
      _dogSize = dogSize;
   }
   virtual void setEars(string type)      // virtual function
   {
      _earType = type;
   }

private:
   string _dogSize, _earType;
   int _legs;
   bool _bark;

};

class breed : public dog
{
public:
   breed( string color, string size)
   {
      _color = color;
      setDogSize(size);
   }

   string getColor()
   {
      return _color;
   }

   // virtual function redefined
   void setEars(string length, string type)
   {
      _earLength = length;
      _earType = type;
   }

protected:
   string _color, _earLength, _earType;
};

int main()
{
   dog mongrel;
   breed labrador("yellow", "large");
   mongrel.setEars("pointy");
   labrador.setEars("long", "floppy");
   cout << "Cody is a " << labrador.getColor() << " labrador" << endl;
}
```

## <a name="see-also"></a>另请参阅

[关键字](../cpp/keywords-cpp.md)<br/>
[类和结构](../cpp/classes-and-structs-cpp.md)
