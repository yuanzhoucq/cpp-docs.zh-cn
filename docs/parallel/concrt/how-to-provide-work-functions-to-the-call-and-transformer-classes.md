---
title: 如何：为 call 和 transformer 类提供工作函数
ms.date: 11/04/2016
helpviewer_keywords:
- call class, example
- using the transformer class [Concurrency Runtime]
- using the call class [Concurrency Runtime]
ms.assetid: df715ce4-8507-41ca-b204-636d11707a73
ms.openlocfilehash: 4d2b7b3c88b51003a96526ef14d9940a8c26c3b3
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142491"
---
# <a name="how-to-provide-work-functions-to-the-call-and-transformer-classes"></a>如何：为 call 和 transformer 类提供工作函数

本主题演示了向[concurrency：： call](../../parallel/concrt/reference/call-class.md)和[concurrency：：变压器](../../parallel/concrt/reference/transformer-class.md)类提供工作函数的几种方法。

第一个示例演示如何将 lambda 表达式传递给 `call` 的对象。 第二个示例演示如何将函数对象传递到 `call` 的对象。 第三个示例演示如何将类方法绑定到 `call` 的对象。

为了举例说明，本主题中的每个示例都使用 `call` 类。 有关使用 `transformer` 类的示例，请参阅[如何：在数据管道中使用转换器](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)。

## <a name="example"></a>示例

下面的示例演示了一种使用 `call` 类的常用方法。 此示例将 lambda 函数传递到 `call` 构造函数。

[!code-cpp[concrt-call-lambda#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_1.cpp)]

本示例生成以下输出。

```Output
13 squared is 169.
```

## <a name="example"></a>示例

下面的示例与上一个示例类似，不同之处在于它将 `call` 类和函数对象（函子）结合使用。

[!code-cpp[concrt-call-functor#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_2.cpp)]

## <a name="example"></a>示例

下面的示例与上一个示例类似，只不过它使用[std：： bind1st](../../standard-library/functional-functions.md#bind1st)和[std：： mem_fun](../../standard-library/functional-functions.md#mem_fun)函数将 `call` 对象绑定到类方法。

如果必须将 `call` 或 `transformer` 对象绑定到特定类方法而不是函数调用运算符，请使用此方法 `operator()`。

[!code-cpp[concrt-call-method#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_3.cpp)]

您还可以将 `bind1st` 函数的结果分配给[std：： function](../../standard-library/function-class.md)对象，或使用 `auto` 关键字，如下面的示例中所示。

[!code-cpp[concrt-call-method#2](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_4.cpp)]

## <a name="compiling-the-code"></a>编译代码

复制代码示例并将其粘贴到 Visual Studio 项目中，或粘贴到一个名为 `call.cpp` 的文件中，然后在 Visual Studio 命令提示符窗口中运行以下命令。

> **cl/EHsc 调用 .cpp**

## <a name="see-also"></a>另请参阅

[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[如何：在数据管道中使用转换器](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br/>
[call 类](../../parallel/concrt/reference/call-class.md)<br/>
[transformer 类](../../parallel/concrt/reference/transformer-class.md)
