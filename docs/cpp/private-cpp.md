---
title: private (C++)
ms.date: 11/04/2016
f1_keywords:
- private_cpp
helpviewer_keywords:
- private keyword [C++]
ms.assetid: 94e99983-46a5-4e21-800c-28f8a7c6a8ff
ms.openlocfilehash: d6dc1ca309c096a4f5e857ade3d7550749991f3f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366202"
---
# <a name="private-c"></a>private (C++)

## <a name="syntax"></a>语法

```
private:
   [member-list]
private base-class
```

## <a name="remarks"></a>备注

在类成员列表之前，**私有**关键字指定这些成员只能从类的成员函数和朋友访问。 这适用于声明到下一个访问指示符或类的末尾的所有成员。

在基类名称之前，**私有**关键字指定基类的公共和受保护成员是派生类的私有成员。

类中成员的默认访问是私有的。 结构或联合中成员的默认访问是公共的。

基类的默认访问对于类是私有的，而对于结构是公共的。  联合不能具有基类。

有关相关信息，请参阅[控制对类成员的访问](member-access-control-cpp.md)中[的朋友](../cpp/friend-cpp.md)、[公共](../cpp/public-cpp.md)、[受保护](../cpp/protected-cpp.md)和成员访问表。

## <a name="clr-specific"></a>/clr 专用

在 CLR 类型中，C++访问指定器关键字（**公共**、**私有**和**受保护**）可能会影响类型和方法对程序集的可见性。 有关详细信息，请参阅[成员访问控制](member-access-control-cpp.md)。

> [!NOTE]
> 使用[/LN](../build/reference/ln-create-msil-module.md)编译的文件不受此行为的影响。 在这种情况下，所有托管类（公共或私有）都将可见。

## <a name="end-clr-specific"></a>END /clr 专用

## <a name="example"></a>示例

```cpp
// keyword_private.cpp
class BaseClass {
public:
   // privMem accessible from member function
   int pubFunc() { return privMem; }
private:
   void privMem;
};

class DerivedClass : public BaseClass {
public:
   void usePrivate( int i )
      { privMem = i; }   // C2248: privMem not accessible
                         // from derived class
};

class DerivedClass2 : private BaseClass {
public:
   // pubFunc() accessible from derived class
   int usePublic() { return pubFunc(); }
};

int main() {
   BaseClass aBase;
   DerivedClass aDerived;
   DerivedClass2 aDerived2;
   aBase.privMem = 1;     // C2248: privMem not accessible
   aDerived.privMem = 1;  // C2248: privMem not accessible
                          //    in derived class
   aDerived2.pubFunc();   // C2247: pubFunc() is private in
                          //    derived class
}
```

## <a name="see-also"></a>另请参阅

[控制对类成员的访问](member-access-control-cpp.md)<br/>
[Keywords](../cpp/keywords-cpp.md)
