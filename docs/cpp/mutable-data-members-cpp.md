---
title: 可变数据成员 （C++） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- mutable_cpp
dev_langs:
- C++
helpviewer_keywords:
- mutable keyword [C++]
ms.assetid: ebe89746-3d36-43a8-8d69-f426af23f551
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de0a208341e6a687d1319c4d8d60cc8671555dd6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106983"
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