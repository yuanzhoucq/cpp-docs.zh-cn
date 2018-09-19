---
title: 公共 （C++） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- public_cpp
dev_langs:
- C++
helpviewer_keywords:
- public keyword [C++]
ms.assetid: f3e10a59-39f6-4bcd-827e-3e99f8f89497
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7ec52069f55ad742bab8378be2aa33d2616244a7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110804"
---
# <a name="public-c"></a>public (C++)

## <a name="syntax"></a>语法

```
public:
   [member-list]
public base-class
```

## <a name="remarks"></a>备注

在前面的类成员的列表时**公共**关键字指定这些成员是可从任何函数访问。 这适用于声明到下一个访问指示符或类的末尾的所有成员。

当基类名称前面**公共**关键字指定基类的公共和受保护成员为公共和受保护的派生类分别成员。

类中成员的默认访问是私有的。 结构或联合中成员的默认访问是公共的。

基类的默认访问对于类是私有的，而对于结构是公共的。  联合不能具有基类。

有关详细信息，请参阅[私有](../cpp/private-cpp.md)，[保护](../cpp/protected-cpp.md)，[友元](../cpp/friend-cpp.md)，和中的成员访问表[控制对类成员的访问](member-access-control-cpp.md).

## <a name="clr-specific"></a>/clr 专用

在 CLR 类型中，c + + 访问说明符关键字 (**公共**，**专用**，并**保护**) 可能会影响的类型和方法与程序集相关的可见性。 有关详细信息，请参阅[成员访问控制](member-access-control-cpp.md)。

> [!NOTE]
>  使用文件编译[/LN](../build/reference/ln-create-msil-module.md)不受此行为。 在这种情况下，所有托管类（公共或私有）都将可见。

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

## <a name="see-also"></a>请参阅

[控制对类成员的访问](member-access-control-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)