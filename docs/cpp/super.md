---
title: __super
ms.date: 11/04/2016
f1_keywords:
- __super_cpp
helpviewer_keywords:
- __super keyword [C++]
ms.assetid: f0957c31-9256-405b-b402-cad182404b5f
ms.openlocfilehash: a69d177bb83ce404a18d50c8f966be5d81f5fa72
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62330526"
---
# <a name="super"></a>__super

**Microsoft 专用**

允许您显式说明要为正在重写的函数调用基类实现。

## <a name="syntax"></a>语法

```
__super::member_function();
```

## <a name="remarks"></a>备注

在重载决策阶段将考虑所有可访问的基类方法，可提供最佳匹配项的函数就是调用的函数。

**__super**只能出现在成员函数体内。

**__super**不能一起使用声明。 请参阅[using 声明](../cpp/using-declaration.md)有关详细信息。

通过引入[属性](../windows/attributes/attributes-alphabetical-reference.md)注入代码中，你的代码可能包含一个或多个基类，但可能不知道其名称中包含你想要调用的方法。

## <a name="example"></a>示例

```cpp
// deriv_super.cpp
// compile with: /c
struct B1 {
   void mf(int) {}
};

struct B2 {
   void mf(short) {}

   void mf(char) {}
};

struct D : B1, B2 {
   void mf(short) {
      __super::mf(1);   // Calls B1::mf(int)
      __super::mf('s');   // Calls B2::mf(char)
   }
};
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[关键字](../cpp/keywords-cpp.md)