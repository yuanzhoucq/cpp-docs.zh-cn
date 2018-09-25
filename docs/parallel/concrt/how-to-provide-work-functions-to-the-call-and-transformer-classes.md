---
title: 如何： 为 call 和 transformer 类提供工作函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- call class, example
- using the transformer class [Concurrency Runtime]
- using the call class [Concurrency Runtime]
ms.assetid: df715ce4-8507-41ca-b204-636d11707a73
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3102947009780f6f4e735b70506c5b2dc02f416b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438959"
---
# <a name="how-to-provide-work-functions-to-the-call-and-transformer-classes"></a>如何：为 call 和 transformer 类提供工作函数

本主题说明了通过多种方法提供工作函数[concurrency:: call](../../parallel/concrt/reference/call-class.md)并[concurrency:: transformer](../../parallel/concrt/reference/transformer-class.md)类。

第一个示例演示如何将传递到 lambda 表达式`call`对象。 第二个示例演示如何将传递到一个函数对象`call`对象。 第三个示例演示如何将绑定到的类方法`call`对象。

本主题中的每个示例图中，对于使用`call`类。 有关使用示例`transformer`类，请参阅[如何： 在数据管道中的使用转换器](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)。

## <a name="example"></a>示例

下面的示例演示一种常见使用方式`call`类。 此示例将传递到 lambda 函数`call`构造函数。

[!code-cpp[concrt-call-lambda#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_1.cpp)]

本示例生成以下输出。

```Output
13 squared is 169.
```

## <a name="example"></a>示例

下面的示例类似于前一个，只不过它使用`call`以及函数对象 （伪函数） 的类。

[!code-cpp[concrt-call-functor#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_2.cpp)]

## <a name="example"></a>示例

下面的示例类似于前一个，只不过它使用[std::bind1st](../../standard-library/functional-functions.md#bind1st)并[std::mem_fun](../../standard-library/functional-functions.md#mem_fun)函数绑定`call`类方法的对象。

如果您需要将绑定，请使用此技术`call`或`transformer`对象对特定类方法而不是函数调用运算符， `operator()`。

[!code-cpp[concrt-call-method#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_3.cpp)]

你还可以分配的结果`bind1st`函数来[std:: function](../../standard-library/function-class.md)对象或使用`auto`关键字，如以下示例所示。

[!code-cpp[concrt-call-method#2](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_4.cpp)]

## <a name="compiling-the-code"></a>编译代码

复制示例代码并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`call.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。

**cl.exe /EHsc call.cpp**

## <a name="see-also"></a>请参阅

[异步代理库](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[如何：在数据管道中使用转换器](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br/>
[call 类](../../parallel/concrt/reference/call-class.md)<br/>
[transformer 类](../../parallel/concrt/reference/transformer-class.md)
