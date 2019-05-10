---
title: 可变数据成员 (C++)
ms.date: 11/04/2016
f1_keywords:
- mutable_cpp
helpviewer_keywords:
- mutable keyword [C++]
ms.assetid: ebe89746-3d36-43a8-8d69-f426af23f551
ms.openlocfilehash: 8d592eb97f70bfc26c075317c57ec4d5c78e3956
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301586"
---
# <a name="mutable-data-members-c"></a>可变数据成员 (C++)

此关键字只能应用于类的非静态和非常量数据成员。 如果声明数据成员**可变**，然后是合法将值分配到此数据成员从**const**成员函数。

## <a name="syntax"></a>语法

```
mutable member-variable-declaration;
```

## <a name="remarks"></a>备注

例如，下面的代码由于将编译没有错误`m_accessCount`已声明为**可变**，并因此可以通过修改`GetFlag`即使`GetFlag`是 const 成员函数。

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

## <a name="see-also"></a>请参阅

[关键字](../cpp/keywords-cpp.md)