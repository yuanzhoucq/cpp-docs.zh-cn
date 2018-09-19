---
title: 编译器错误 C3066 |Microsoft Docs
ms.custom: ''
ms.date: 03/28/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3066
dev_langs:
- C++
helpviewer_keywords:
- C3066
ms.assetid: 226f6de5-c4c5-41e2-b31a-2e30a37fbbeb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 35600fae9a689b32cca9c327645a0e0c1bb91a25
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084609"
---
# <a name="compiler-error-c3066"></a>编译器错误 C3066

有很多方法可以调用此类型的对象用这些自变量

编译器检测到涉及代理项的不明确的函数调用。

下面的示例生成 C3066:

```
// C3066.cpp
template <class T, class U> void func(T*, U*){}

typedef void (*PF)(const int*, const char*);
typedef void (*PF1)(const int*, volatile char*);

struct A {
   operator PF() const {
      return func;
   }

   operator PF1() {
      return func;
   }

   operator PF1() const  {
      return func;
   }

};

int main() {
   A a;
   int i;
   char c;

   a(&i, &c);   // C3066
   a(&i, (const char *) &c);   // OK
}
```

## <a name="copy-list-initialization"></a>复制列表初始化

在 Visual Studio 2015 中，编译器以与常规复制初始化相同的方式错误地处理复制列表初始化；它只考虑将转换构造函数用于重载决策。 在以下示例中，Visual Studio 2015 选择 MyInt(23)，但 Visual Studio 2017 正确引发错误。

```
// From http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_closed.html#1228
struct MyList {
       explicit MyStore(int initialCapacity);
};

struct MyInt {
       MyInt(int i);
};

struct Printer {
       void operator()(MyStore const& s);
       void operator()(MyInt const& i);
};

void f() {
       Printer p;
       p({ 23 }); // C3066: there are multiple ways that an object of this type can be called with these arguments
}
```