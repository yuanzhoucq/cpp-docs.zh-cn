---
title: 用于编译时 （现代 C++） 封装的 Pimpl |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c3e8a90a-b328-4990-82bb-e1b147f76e07
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 83b01a58745185499ac02a254a207fac2779be26
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058999"
---
# <a name="pimpl-for-compile-time-encapsulation-modern-c"></a>用于编译时封装的 Pimpl（现代 C++）

*Pimpl 惯用语法*现代的 C++ 技术，可隐藏实现，以便最大程度减少耦合，从而单独的接口。 Pimpl 是短的"指向的实现。" 你已可能熟悉的概念，但是知道它通过类似 Cheshire Cat 或编译器防火墙惯用语法其他名称。

## <a name="why-use-pimpl"></a>为什么要使用的 pimpl？

下面是 pimpl 惯用语法可以如何改进软件开发生命周期：

- 编译依赖项的最小化。

- 接口和实现分离。

- 可移植性。

## <a name="pimpl-header"></a>Pimpl 标头

```cpp
// my_class.h
class my_class {
   //  ... all public and protected stuff goes here ...
private:
   class impl; unique_ptr<impl> pimpl; // opaque type here
};
```

重新生成级联和脆弱的对象布局，可避免 pimpl 惯用语法。 它非常适合用于 （间接） 受欢迎的类型。

## <a name="pimpl-implementation"></a>Pimpl 实现

定义`impl`.cpp 文件中的类。

```cpp
// my_class.cpp
class my_class::impl {  // defined privately here
  // ... all private data and functions: all of these
  //     can now change without recompiling callers ...
};
my_class::my_class(): pimpl( new impl )
{
  // ... set impl values ...
}
```

## <a name="best-practices"></a>最佳做法

考虑添加对非引发交换专用化的支持。

## <a name="see-also"></a>请参阅

[欢迎回到 C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 语言参考](../cpp/cpp-language-reference.md)<br/>
[C++ 标准库](../standard-library/cpp-standard-library-reference.md)