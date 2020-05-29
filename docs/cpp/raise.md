---
title: __raise
ms.date: 11/04/2016
f1_keywords:
- __raise
- __raise_cpp
helpviewer_keywords:
- __raise keyword [C++]
ms.assetid: 6f1ae418-5f0f-48b6-9f6e-8ea7e66b239a
ms.openlocfilehash: eb3ab24378071663b2a6a1abab700b81c3172419
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317224"
---
# <a name="__raise"></a>__raise

强调一个事件的调用站点。

## <a name="syntax"></a>语法

```
__raise method-declarator;
```

## <a name="remarks"></a>备注

在托管代码中，事件只能从定义它的类中引发。 有关详细信息，请参阅[事件](../extensions/event-cpp-component-extensions.md)。

如果调用非事件，关键字 **__raise**会导致发出错误。

> [!NOTE]
> 模板类或结构不能包含事件。

## <a name="example"></a>示例

```cpp
// EventHandlingRef_raise.cpp
struct E {
   __event void func1();
   void func1(int) {}

   void func2() {}

   void b() {
      __raise func1();
      __raise func1(1);  // C3745: 'int Event::bar(int)':
                         // only an event can be 'raised'
      __raise func2();   // C3745
   }
};

int main() {
   E e;
   __raise e.func1();
   __raise e.func1(1);  // C3745
   __raise e.func2();   // C3745
}
```

## <a name="see-also"></a>另请参阅

[Keywords](../cpp/keywords-cpp.md)<br/>
[事件处理](../cpp/event-handling.md)<br/>
[适用于运行时平台的组件扩展](../extensions/component-extensions-for-runtime-platforms.md)
