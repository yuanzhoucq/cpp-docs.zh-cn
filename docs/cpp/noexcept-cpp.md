---
title: noexcept (C++)
ms.date: 11/19/2019
f1_keywords:
- noexcept_cpp
ms.assetid: df24edb9-c6a6-4e37-9914-fd5c0c3716a8
ms.openlocfilehash: 5e8d58ed246b0143dc3d3be545cd796a4c3d60ed
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245631"
---
# <a name="noexcept-c"></a>noexcept (C++)

**C + + 11：** 指定函数是否可能会引发异常。

## <a name="syntax"></a>语法

> *noexcept*： &nbsp;&nbsp;&nbsp;&nbsp;**noexcept** &nbsp;&nbsp;&nbsp;&nbsp;**noexcept （** *常量-表达式* **）**

### <a name="parameters"></a>参数

*常量表达式*<br/>
类型为**bool**的常量表达式，它表示可能的异常类型集是否为空。 无条件版本等效于 `noexcept(true)`。

## <a name="remarks"></a>备注

*Noexcept 表达式*是一种*异常规范*，它是一个函数声明的后缀，表示一组类型，这些类型可能由任何退出函数的异常的异常处理程序匹配。 一元条件运算符 `noexcept(`*constant_expression*`)` 其中*constant_expression*生成**true**，而其无条件同义词**noexcept**，则指定可以退出函数的可能的异常类型集为空。 也就是说，函数永远不会引发异常，并且永远不允许将异常传播到其作用域外。 运算符 `noexcept(`*constant_expression*`)`，其中*constant_expression*产生**false**，或缺少异常规范（对于析构函数或释放函数除外），指示可以退出函数的可能异常集是所有类型的集合。

仅当函数直接或间接调用的所有函数也是**noexcept**或**const**时，才将其标记为**noexcept** 。 编译器不一定要检查可能冒泡到**noexcept**函数的异常的每个代码路径。 如果异常退出了标记为 `noexcept`的函数的外部范围，则会立即调用[std：： terminate](../standard-library/exception-functions.md#terminate) ，并且不保证将调用任何范围内对象的析构函数。 使用**noexcept**而不是动态异常说明符 `throw()`，这在标准中现已弃用。 建议将 `noexcept` 应用到任何从不允许异常传播调用堆栈的函数。 将函数声明为**noexcept**时，编译器会使编译器在多个不同的上下文中生成更高效的代码。 有关详细信息，请参阅[异常规范](exception-specifications-throw-cpp.md)。

## <a name="example"></a>示例

如果要复制的对象是普通的旧数据类型（POD），则可将复制其参数的模板函数声明为**noexcept** 。 此类函数可以如下声明：

```cpp
#include <type_traits>

template <typename T>
T copy_object(const T& obj) noexcept(std::is_pod<T>)
{
   // ...
}
```

## <a name="see-also"></a>另请参阅

[异常C++和错误处理的新式最佳实践](errors-and-exception-handling-modern-cpp.md)<br/>
[异常规范（throw，noexcept）](exception-specifications-throw-cpp.md)