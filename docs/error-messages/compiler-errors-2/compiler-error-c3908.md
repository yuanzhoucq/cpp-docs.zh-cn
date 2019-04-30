---
title: 编译器错误 C3908
ms.date: 11/04/2016
f1_keywords:
- C3908
helpviewer_keywords:
- C3908
ms.assetid: 3c322482-c79e-4197-a578-2ad9bc379d1a
ms.openlocfilehash: e11d830c3d662ea424caadeb50df669700f8c78f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406543"
---
# <a name="compiler-error-c3908"></a>编译器错误 C3908

访问级别限制性比 construct

属性访问器方法 （get 或 set） 不能具有限制性比属性本身上指定的访问权限的访问权限。  同样，对于事件访问器方法。

有关详细信息，请参阅[属性](../../extensions/property-cpp-component-extensions.md)并[事件](../../extensions/event-cpp-component-extensions.md)。

下面的示例生成 C3908:

```
// C3908.cpp
// compile with: /clr
ref class X {
protected:
   property int i {
   public:   // C3908 property i is protected
      int get();
   private:
      void set(int);   // OK more restrictive
   };
};
```