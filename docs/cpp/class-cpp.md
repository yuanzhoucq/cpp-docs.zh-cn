---
title: class (C++)
ms.date: 11/04/2016
f1_keywords:
- class_cpp
helpviewer_keywords:
- class types [C++], class statements
- class keyword [C++]
ms.assetid: dd23c09f-6598-4069-8bff-69c7f2518b9f
ms.openlocfilehash: 4404767fc6cf07c2a7a23d460e13bb191fef387a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555137"
---
# <a name="class-c"></a>class (C++)

**类**关键字声明的类类型或定义类类型的对象。

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

*模板规范*<br/>
可选模板规范。 有关详细信息，请参阅[模板](templates-cpp.md)。

*class*<br/>
**类**关键字。

*ms 声明规范*<br/>
可选存储类规范。 有关详细信息，请参阅[__declspec](../cpp/declspec.md)关键字。

*标记*<br/>
提供给类的类型名称。 标记将变成类的范围内的保留的字。 标记是可选项。 如果省略，则定义匿名类。 有关详细信息，请参阅[匿名类类型](../cpp/anonymous-class-types.md)。

*基础列表*<br/>
类或结构，此类将从中派生其成员的可选列表。 请参阅[基类](../cpp/base-classes.md)有关详细信息。 每个基的类或结构名称的前面可具有访问说明符 ([公共](../cpp/public-cpp.md)，[专用](../cpp/private-cpp.md)，[保护](../cpp/protected-cpp.md)) 和[虚拟](../cpp/virtual-cpp.md)关键字。 请参阅中的成员访问表[控制对类成员的访问](member-access-control-cpp.md)有关详细信息。

*成员的列表*<br/>
类成员的列表。 请参阅[类成员概述](../cpp/class-member-overview.md)有关详细信息。

*声明符*<br/>
指定类类型的一个或多个实例的名称的声明符列表。 如果类的所有数据成员声明符可以包含初始值设定项列表**公共**。 这是更常见的结构，其数据成员均**公共**默认情况下，比类。 请参阅[的声明符概述](../cpp/overview-of-declarators.md)有关详细信息。

## <a name="remarks"></a>备注

有关详细信息的类一般情况下，请参阅以下主题之一：

- [struct](../cpp/struct-cpp.md)

- [union](../cpp/unions.md)

- [__multiple_inheritance](../cpp/inheritance-keywords.md)

- [__single_inheritance](../cpp/inheritance-keywords.md)

- [__virtual_inheritance](../cpp/inheritance-keywords.md)

有关托管的类和结构的信息，请参阅[类和结构](../windows/classes-and-structs-cpp-component-extensions.md)

## <a name="example"></a>示例

```cpp
// class.cpp
// compile with: /EHsc
// Example of the class keyword
// Exhibits polymorphism/virtual functions.

#include <iostream>
#include <string>
#define TRUE = 1
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

## <a name="see-also"></a>请参阅

[关键字](../cpp/keywords-cpp.md)<br/>
[类和结构](../cpp/classes-and-structs-cpp.md)