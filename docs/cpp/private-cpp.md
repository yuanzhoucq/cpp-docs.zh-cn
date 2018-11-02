---
title: private (C++)
ms.date: 11/04/2016
f1_keywords:
- private_cpp
helpviewer_keywords:
- private keyword [C++]
ms.assetid: 94e99983-46a5-4e21-800c-28f8a7c6a8ff
ms.openlocfilehash: 19ea551f625cac02e639753a976eddb7a5fa164b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622269"
---
# <a name="private-c"></a>private (C++)

## <a name="syntax"></a>语法

```
private:
   [member-list]
private base-class
```

## <a name="remarks"></a>备注

在前面的类成员的列表时**专用**关键字指定这些成员是只能从成员函数和类的友元访问。 这适用于声明到下一个访问指示符或类的末尾的所有成员。

当基类名称前面**专用**关键字指定基类的公共和受保护成员为派生类的私有成员。

类中成员的默认访问是私有的。 结构或联合中成员的默认访问是公共的。

基类的默认访问对于类是私有的，而对于结构是公共的。  联合不能具有基类。

有关相关信息，请参阅[友元](../cpp/friend-cpp.md)，[公共](../cpp/public-cpp.md)，[保护](../cpp/protected-cpp.md)，和中的成员访问表[控制对类成员访问](member-access-control-cpp.md).

## <a name="clr-specific"></a>/clr 专用

在 CLR 类型中，c + + 访问说明符关键字 (**公共**，**专用**，并**保护**) 可能会影响的类型和方法与程序集相关的可见性。 有关详细信息，请参阅[成员访问控制](member-access-control-cpp.md)。

> [!NOTE]
>  使用文件编译[/LN](../build/reference/ln-create-msil-module.md)不受此行为。 在这种情况下，所有托管类（公共或私有）都将可见。

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

## <a name="see-also"></a>请参阅

[控制对类成员的访问](member-access-control-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)