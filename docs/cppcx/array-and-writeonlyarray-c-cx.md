---
title: Array 和 WriteOnlyArray (C++/CX)
ms.date: 01/22/2017
ms.assetid: ef7cc5f9-cae6-4636-8220-f789e5b6aea4
ms.openlocfilehash: 1980fbcd1e2fa8cdaa48e00d2e7de9e45ac96a92
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231021"
---
# <a name="array-and-writeonlyarray-ccx"></a>Array 和 WriteOnlyArray (C++/CX)

可以自由使用常规 C 样式数组或 [`std::array`](../standard-library/array-class-stl.md) c + +/cx 程序（尽管通常是 [`std::vector`](../standard-library/vector-class.md) 更好的选择），但是，在元数据中发布的任何 API 中，必须将 C 样式数组或向量转换为 [`Platform::Array`](../cppcx/platform-array-class.md) 或类型， [`Platform::WriteOnlyArray`](../cppcx/platform-writeonlyarray-class.md) 具体取决于其使用方式。 [`Platform::Array`](../cppcx/platform-array-class.md)类型既不像这样强大，也不像那样强大 [`std::vector`](../standard-library/vector-class.md) ，因此，一般原则是，应避免在对数组元素执行大量操作的内部代码中使用该类型。

以下数组类型可在 ABI 中传递：

1. `const Platform::Array^`

1. `Platform::Array^*`

1. `Platform::WriteOnlyArray`

1. 返回值`Platform::Array^`

使用这些数组类型可实现由 Windows 运行时定义的三种数组模式。

PassArray
在调用方将数组传递给方法时使用。 C + + 输入参数类型为 **`const`** [`Platform::Array`](../cppcx/platform-array-class.md) \<T> 。

FillArray
在调用方传递一个数组以便方法填充时使用。 C + + 输入参数类型为 [`Platform::WriteOnlyArray`](../cppcx/platform-writeonlyarray-class.md) \<T> 。

ReceiveArray
在调用方接收方法分配的数组时使用。 在 C++/CX 中，你可以在返回值中将数组返回为 Array^，也可以将其作为类型 Array^* 的输出参数返回。

## <a name="passarray-pattern"></a>PassArray 模式

当客户端代码将数组传递给 c + + 方法并且方法不修改它时，该方法接受数组作为 `const Array^` 。 在 Windows 运行时应用程序二进制接口（ABI）级别，这称为*PassArray*。 下一个示例演示如何将 JavaScript 中分配的数组传递给读取它的 C++ 函数。

[!code-javascript[cx_arrays#101](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_1.js)]

下面的代码片段演示 C++ 方法：

[!code-cpp[cx_arrays#01](../cppcx/codesnippet/CPP/js-array/class1.cpp#01)]

## <a name="receivearray-pattern"></a>ReceiveArray 模式

在*ReceiveArray*模式中，客户端代码声明一个数组，并将其传递给为其分配内存的方法并对其进行初始化。 C + + 输入参数类型是指向 hat 的指针： `Array<T>^*` 。 下面的示例演示如何在 JavaScript 中声明一个数组对象并将其传递给一个 C++ 函数，该函数分配内存，初始化元素，并将其返回到 JavaScript。 JavaScript 将分配的数组视为返回值，而 C++ 将其视为输出参数。

[!code-javascript[cx_arrays#102](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_3.js)]

下面的代码片段演示实现 C++ 方法的两种方式：

[!code-cpp[cx_arrays#02](../cppcx/codesnippet/CPP/js-array/class1.cpp#02)]

## <a name="fill-arrays"></a>填充数组

若要在调用方分配一个数组，并在被调用方初始化或修改它，请使用 `WriteOnlyArray`。 下一个示例演示如何实现使用 `WriteOnlyArray` 的 C++ 函数并从 JavaScript 调用它。

[!code-javascript[cx_arrays#103](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_5.js)]

下面的代码片段演示实现 C++ 方法的方式：

[!code-cpp[cx_arrays#03](../cppcx/codesnippet/CPP/js-array/class1.cpp#03)]

## <a name="array-conversions"></a>数组转换

此示例演示如何使用 [`Platform::Array`](../cppcx/platform-array-class.md) 来构造其他类型的集合：

[!code-cpp[cx_arrays#05](../cppcx/codesnippet/CPP/js-array/class1.cpp#05)]

下一个示例演示如何 [`Platform::Array`](../cppcx/platform-array-class.md) 从 C 样式数组构造，并从公共方法返回它。

[!code-cpp[cx_arrays#06](../cppcx/codesnippet/CPP/js-array/class1.cpp#06)]

## <a name="jagged-arrays"></a>交错数组

Windows 运行时类型系统不支持交错数组的概念，因此无法在公共方法中将 `IVector<Platform::Array<T>>` 作为返回值或方法参数传递。 要跨 ABI 传递交错数组或一系列序列，请使用 `IVector<IVector<T>^>`。

## <a name="use-arrayreference-to-avoid-copying-data"></a>使用 ArrayReference 可避免复制数据

在某些情况下，如果数据正在通过 ABI 传递到 [`Platform::Array`](../cppcx/platform-array-class.md) 中，并且你最终需要在 C 样式数组中处理数据以提高效率，则可以使用[Platform：： ArrayReference](../cppcx/platform-arrayreference-class.md)来避免额外的复制操作。 [`Platform::ArrayReference`](../cppcx/platform-arrayreference-class.md)将作为参数传递给采用的参数时 `Platform::Array` ， `ArrayReference` 会将数据直接存储到指定的 C 样式数组中。 需要了解的是， `ArrayReference` 未锁定源数据，因此，如果在调用完成之前在另一个线程上修改或删除此数据，则结果将是未定义的。

下面的代码段演示如何将操作的结果复制 [`DataReader`](/uwp/api/windows.storage.streams.datareader) 到 `Platform::Array` （通常模式）中，以及如何替代 `ArrayReference` 以将数据直接复制到 C 样式数组中：

[!code-cpp[cx_arrays#07](../cppcx/codesnippet/CPP/js-array/class1.h#07)]

## <a name="avoid-exposing-an-array-as-a-property"></a>避免将数组公开为属性

通常，应避免将 `Platform::Array` 类型公开为 ref 类中的属性，因为将返回整个数组，即使在客户端代码仅尝试访问单个元素时也是如此。 如果需要将序列容器公开为公共 ref 类中的属性， [`Windows::Foundation::IVector`](/uwp/api/windows.foundation.collections.ivector-1) 则是更好的选择。 在私有或内部 Api 中（未发布到元数据），请考虑使用标准 c + + 容器（如） [`std::vector`](../standard-library/vector-class.md) 。

## <a name="see-also"></a>另请参阅

[类型系统](../cppcx/type-system-c-cx.md)<br/>
[C + +/CX 语言参考](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[命名空间引用](../cppcx/namespaces-reference-c-cx.md)
