---
title: 用于编译时封装的 Pimpl（现代 C++）
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c3e8a90a-b328-4990-82bb-e1b147f76e07
ms.openlocfilehash: 6e114e2802dd4b2e5d1497867e2224be90c4752d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396101"
---
# <a name="pimpl-for-compile-time-encapsulation-modern-c"></a>用于编译时封装的 Pimpl（现代 C++）

*Pimpl 惯用语法*是新式 C++ 技术，可隐藏实现，以最大程度减少耦合，并分离出接口。 Pimpl 是"pointer to implementation"的缩写。 你可能已通过 Cheshire Cat 或 Compiler Firewall 惯用语法等名称了解了这一概念。

## <a name="why-use-pimpl"></a>为什么要使用 pimpl？

下面是 pimpl 惯用语法优化软件开发生命周期的方式：

- 编译依赖项的最小化。

- 接口和实现分离。

- 可移植性。

## <a name="pimpl-header"></a>Pimpl 头文件

```cpp
// my_class.h
class my_class {
   //  ... all public and protected stuff goes here ...
private:
   class impl; unique_ptr<impl> pimpl; // opaque type here
};
```

pimpl 可避免重新生成级联和脆弱的对象布局。 它非常适合（以及物方式）用于常见类型。

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

## <a name="best-practices"></a>最佳实践

考虑添加对非引发交换专用化的支持。

## <a name="see-also"></a>请参阅

[欢迎回到 C++（现代 C++）](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 语言参考](../cpp/cpp-language-reference.md)<br/>
[C++ 标准库](../standard-library/cpp-standard-library-reference.md)
