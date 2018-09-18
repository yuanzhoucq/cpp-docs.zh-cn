---
title: 编译器错误 C3908 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3908
dev_langs:
- C++
helpviewer_keywords:
- C3908
ms.assetid: 3c322482-c79e-4197-a578-2ad9bc379d1a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7591b8ab5f8495b6af866e23e7a169b0f9cd29a6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047312"
---
# <a name="compiler-error-c3908"></a>编译器错误 C3908

访问级别限制性比 construct

属性访问器方法 （get 或 set） 不能具有限制性比属性本身上指定的访问权限的访问权限。  同样，对于事件访问器方法。

有关详细信息，请参阅[属性](../../windows/property-cpp-component-extensions.md)并[事件](../../windows/event-cpp-component-extensions.md)。

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