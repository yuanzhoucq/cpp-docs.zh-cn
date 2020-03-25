---
title: 可变数据成员 (C++)
ms.date: 11/04/2016
f1_keywords:
- mutable_cpp
helpviewer_keywords:
- mutable keyword [C++]
ms.assetid: ebe89746-3d36-43a8-8d69-f426af23f551
ms.openlocfilehash: db3a9594a77a9ada971213eaea74a9842bd96a54
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179336"
---
# <a name="mutable-data-members-c"></a>可变数据成员 (C++)

此关键字只能应用于类的非静态和非常量数据成员。 如果数据成员被声明为**可变**的，则从**const**成员函数向此数据成员赋值是合法的。

## <a name="syntax"></a>语法

```
mutable member-variable-declaration;
```

## <a name="remarks"></a>备注

例如，以下代码将在编译时不会出错，因为 `m_accessCount` 已声明为**可变**的，因此可以通过 `GetFlag` 进行修改，即使 `GetFlag` 是 const 成员函数。

```cpp
// mutable.cpp
class X
{
public:
   bool GetFlag() const
   {
      m_accessCount++;
      return m_flag;
   }
private:
   bool m_flag;
   mutable int m_accessCount;
};

int main()
{
}
```

## <a name="see-also"></a>另请参阅

[关键字](../cpp/keywords-cpp.md)
