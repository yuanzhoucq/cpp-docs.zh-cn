---
title: Array 和 WriteOnlyArray (C++/CX)
ms.date: 01/22/2017
ms.assetid: ef7cc5f9-cae6-4636-8220-f789e5b6aea4
ms.openlocfilehash: fd616487bd3c11544f12e84a7dc64f41e63d501a
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57739413"
---
# <a name="array-and-writeonlyarray-ccx"></a>Array 和 WriteOnlyArray (C++/CX)

你可以自由使用常规 C 样式数组或[std:: array](../standard-library/array-class-stl.md)在 C + + /CX 程序 (尽管[std:: vector](../standard-library/vector-class.md)通常是更好的选择)，但在任何 API 中的元数据中发布，您必须将转换为 C 样式数组或到矢量[platform:: array](../cppcx/platform-array-class.md)或[platform:: writeonlyarray](../cppcx/platform-writeonlyarray-class.md)根据使用方式的类型。 [Platform::Array](../cppcx/platform-array-class.md) 类型既不像 [std::vector](../standard-library/vector-class.md)那样高效也不像它那样功能强大，因此，一般原则是，应避免在对数组元素执行大量操作的内部代码中使用该类型。

以下数组类型可在 ABI 中传递：

1. const Platform::Array^

1. Platform::Array^*

1. Platform::WriteOnlyArray

1. return value of Platform::Array^

使用这些数组类型实现的三类数组模式定义的 Windows 运行时。

PassArray 使用调用方将数组传递给方法时。 C + + 输入的参数类型是`const` [platform:: array](../cppcx/platform-array-class.md)\<T >。

调用方传递一个数组以便方法填充时，将使用 FillArray。 C + + 输入的参数类型是[platform:: writeonlyarray](../cppcx/platform-writeonlyarray-class.md)\<T >。

调用方接收方法分配的数组时，将使用 ReceiveArray。 在 C++/CX 中，你可以在返回值中将数组返回为 Array^，也可以将其作为类型 Array^* 的输出参数返回。

## <a name="passarray-pattern"></a>PassArray 模式

当客户端代码将数组传递给一个 C++ 方法，而该方法没有修改它时，该方法接受该数组作为 const Array^。 在 Windows 运行时应用程序二进制接口 (ABI) 级别，这称为 PassArray。 下一个示例演示如何将 JavaScript 中分配的数组传递给读取它的 C++ 函数。

[!code-javascript[cx_arrays#101](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_1.js)]

下面的代码片段演示 C++ 方法：

[!code-cpp[cx_arrays#01](../cppcx/codesnippet/CPP/js-array/class1.cpp#01)]

## <a name="receivearray-pattern"></a>ReceiveArray 模式

在 ReceiveArray 模式中，客户端代码声明一个数组，然后将数组传递给为其分配内存的方法并初始化它。 C + + 输入的参数类型是指针到 hat: `Array<T>^*`。 下面的示例演示如何在 JavaScript 中声明一个数组对象并将其传递给一个 C++ 函数，该函数分配内存，初始化元素，并将其返回到 JavaScript。 JavaScript 将分配的数组视为返回值，而 C++ 将其视为输出参数。

[!code-javascript[cx_arrays#102](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_3.js)]

下面的代码片段演示实现 C++ 方法的两种方式：

[!code-cpp[cx_arrays#02](../cppcx/codesnippet/CPP/js-array/class1.cpp#02)]

## <a name="fill-arrays"></a>填充数组

若要在调用方分配一个数组，并在被调用方初始化或修改它，请使用 `WriteOnlyArray`。 下一个示例演示如何实现使用 `WriteOnlyArray` 的 C++ 函数并从 JavaScript 调用它。

[!code-javascript[cx_arrays#103](../cppcx/codesnippet/JavaScript/array-and-writeonlyarray-c-_5.js)]

下面的代码片段演示实现 C++ 方法的方式：

[!code-cpp[cx_arrays#03](../cppcx/codesnippet/CPP/js-array/class1.cpp#03)]

## <a name="array-conversions"></a>数组转换

以下示例演示如何使用 [Platform::Array](../cppcx/platform-array-class.md) 构造其他类型的集合：

[!code-cpp[cx_arrays#05](../cppcx/codesnippet/CPP/js-array/class1.cpp#05)]

下一示例演示如何根据 C 样式数组构造 [Platform::Array](../cppcx/platform-array-class.md) 并通过公共方法返回它。

[!code-cpp[cx_arrays#06](../cppcx/codesnippet/CPP/js-array/class1.cpp#06)]

## <a name="jagged-arrays"></a>交错数组

Windows 运行时类型系统不支持交错数组的概念，因此无法在公共方法中将 `IVector<Platform::Array<T>>` 作为返回值或方法参数传递。 要跨 ABI 传递交错数组或一系列序列，请使用 `IVector<IVector<T>^>`。

## <a name="use-arrayreference-to-avoid-copying-data"></a>使用 ArrayReference 可避免复制数据

在某些情况下，数据将通过 ABI 传递给 [Platform::Array](../cppcx/platform-array-class.md)，并且你最终需要在 C 样式数组中处理数据以实现较高的效率，对于这些情况你可以使用 [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) 来避免额外的复制操作。 在将 [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) 作为实参传递给采用 `Platform::Array`的形参时， `ArrayReference` 会直接将数据存储到你指定的 C 样式数组中。 需要了解的是， `ArrayReference` 未锁定源数据，因此，如果在调用完成之前在另一个线程上修改或删除此数据，则结果将是未定义的。

下面的代码片段演示如何将 [DataReader](/uwp/api/Windows.Storage.Streams.DataReader) 操作的结果复制到 `Platform::Array` （通常模式）中，以及如何替代 `ArrayReference` 以将数据直接复制到 C 样式数组中：

[!code-cpp[cx_arrays#07](../cppcx/codesnippet/CPP/js-array/class1.h#07)]

## <a name="avoid-exposing-an-array-as-a-property"></a>避免将数组公开为属性

通常，应避免将 `Platform::Array` 类型公开为 ref 类中的属性，因为将返回整个数组，即使在客户端代码仅尝试访问单个元素时也是如此。 当需要将序列容器公开为公共 ref 类的属性时， [Windows::Foundation::IVector](/uwp/api/Windows.Foundation.Collections.IVector_T_) 是更好的选择。 在私有或内部 API 中（未发布到元数据），请考虑使用标准 C++ 容器（如 [std::vector](../standard-library/vector-class.md)）。

## <a name="see-also"></a>请参阅

[类型系统](../cppcx/type-system-c-cx.md)<br/>
[Visual c + + 语言参考](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[命名空间参考](../cppcx/namespaces-reference-c-cx.md)
