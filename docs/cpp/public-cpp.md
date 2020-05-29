---
title: public (C++)
ms.date: 11/04/2016
f1_keywords:
- public_cpp
helpviewer_keywords:
- public keyword [C++]
ms.assetid: f3e10a59-39f6-4bcd-827e-3e99f8f89497
ms.openlocfilehash: bf8293c6a6cf12154b02979de08035807991052c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376054"
---
# <a name="public-c"></a>public (C++)

## <a name="syntax"></a>语法

```
public:
   [member-list]
public base-class
```

## <a name="remarks"></a>备注

在类成员列表之前 **，public**关键字指定可从任何函数访问这些成员。 这适用于声明到下一个访问指示符或类的末尾的所有成员。

在基类名称之前 **，public**关键字指定基类的公共成员和保护成员分别是派生类的公共成员和受保护成员。

类中成员的默认访问是私有的。 结构或联合中成员的默认访问是公共的。

基类的默认访问对于类是私有的，而对于结构是公共的。  联合不能具有基类。

有关详细信息，请参阅[私有](../cpp/private-cpp.md)、[受保护](../cpp/protected-cpp.md)、[好友](../cpp/friend-cpp.md)和成员访问表，[以控制对类成员的访问](member-access-control-cpp.md)。

## <a name="clr-specific"></a>/clr 专用

在 CLR 类型中，C++访问指定器关键字（**公共**、**私有**和**受保护**）可能会影响类型和方法对程序集的可见性。 有关详细信息，请参阅[成员访问控制](member-access-control-cpp.md)。

> [!NOTE]
> 使用[/LN](../build/reference/ln-create-msil-module.md)编译的文件不受此行为的影响。 在这种情况下，所有托管类（公共或私有）都将可见。

## <a name="end-clr-specific"></a>END /clr 专用

## <a name="example"></a>示例

```cpp
// keyword_public.cpp
class BaseClass {
public:
   int pubFunc() { return 0; }
};

class DerivedClass : public BaseClass {};

int main() {
   BaseClass aBase;
   DerivedClass aDerived;
   aBase.pubFunc();       // pubFunc() is accessible
                          //    from any function
   aDerived.pubFunc();    // pubFunc() is still public in
                          //    derived class
}
```

## <a name="see-also"></a>另请参阅

[控制对类成员的访问](member-access-control-cpp.md)<br/>
[Keywords](../cpp/keywords-cpp.md)
