---
title: 如何： 为 call 和 transformer 类提供工作函数 |Microsoft 文档
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
ms.openlocfilehash: ca7948a1258ac1b5193d379dd37f426360edc42e
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-provide-work-functions-to-the-call-and-transformer-classes"></a>如何：为 call 和 transformer 类提供工作函数
本主题演示通过多种方法提供工作函数[concurrency:: call](../../parallel/concrt/reference/call-class.md)和[concurrency:: transformer](../../parallel/concrt/reference/transformer-class.md)类。  
  
 第一个示例演示如何将传递到 lambda 表达式`call`对象。 第二个示例演示如何将传递到一个函数对象`call`对象。 第三个示例演示如何将绑定到类方法`call`对象。  
  
 为进行说明，使用本主题中的每个示例`call`类。 有关示例，使用`transformer`类，请参阅[如何： 在数据管道中的使用 transformer](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示使用的常用方法`call`类。 此示例将传递到 lambda 函数`call`构造函数。  
  
 [!code-cpp[concrt-call-lambda#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_1.cpp)]  
  
 本示例生成以下输出。  
  
```Output  
13 squared is 169.  
```  
  
## <a name="example"></a>示例  
 下面的示例类似于前一个，只不过它使用`call`以及 （函子） 的函数对象的类。  
  
 [!code-cpp[concrt-call-functor#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_2.cpp)]  
  
## <a name="example"></a>示例  

 下面的示例类似于前一个，只不过它使用[std::bind1st](../../standard-library/functional-functions.md#bind1st)和[std::mem_fun](../../standard-library/functional-functions.md#mem_fun)函数绑定`call`对类方法的对象。  

  
 使用此方法，如果必须将绑定`call`或`transformer`对象对特定的类方法而不是函数调用运算符， `operator()`。  
  
 [!code-cpp[concrt-call-method#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_3.cpp)]  
  
 你还可以分配的结果`bind1st`函数来[std:: function](../../standard-library/function-class.md)对象或使用`auto`关键字，如下面的示例中所示。  
  
 [!code-cpp[concrt-call-method#2](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_4.cpp)]  
  
## <a name="compiling-the-code"></a>编译代码  
 复制代码示例并将其粘贴到 Visual Studio 项目中，或将其粘贴在文件中名为`call.cpp`然后在 Visual Studio 命令提示符窗口中运行以下命令。  
  
 **cl.exe /EHsc call.cpp**  
  
## <a name="see-also"></a>请参阅  
 [异步代理库](../../parallel/concrt/asynchronous-agents-library.md)   
 [异步消息块](../../parallel/concrt/asynchronous-message-blocks.md)   
 [如何： 在数据管道中的使用 transformer](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)   
 [call 类](../../parallel/concrt/reference/call-class.md)   
 [transformer 类](../../parallel/concrt/reference/transformer-class.md)
