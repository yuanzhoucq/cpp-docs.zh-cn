---
title: 异常处理 (C + + /cli 和 C + + /cli CX) |Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- structured exception handling [C++], managed exceptions
- Exception class, managed applications
- exception handling
- C++ exception handling
- exception handling, types of
- System::Exception class in managed applications
ms.assetid: ccb11fe8-6938-41ac-b477-a183e85865b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7d070cc223f90f84bd52176ee7e50dbbfa441789
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2018
ms.locfileid: "49328124"
---
# <a name="exception-handling--ccli-and-ccx"></a>异常处理 (C + + /cli 和 C + + /cli CX)

使用应用程序编译`/ZW`编译器选项或`/clr`编译器选项都使用*异常*在程序执行期间处理意外的错误。 以下主题讨论 C++/CX 或 C++/CLI 应用程序中的异常处理。

## <a name="in-this-section"></a>本节内容

[使用托管异常中的基本概念](../dotnet/basic-concepts-in-using-managed-exceptions.md)<br/>
描述引发的异常和使用**尝试**/**捕获**块。

[异常处理行为 /clr 下的差异](../dotnet/differences-in-exception-handling-behavior-under-clr.md)<br/>
讨论与 C++ 异常处理的标准行为的区别。

[finally](../dotnet/finally.md)<br/>
讨论如何使用 finally 关键字。

[如何：定义和安装全局异常处理程序](../dotnet/how-to-define-and-install-a-global-exception-handler.md)<br/>
演示如何捕获未经处理的异常。

[如何：在本机代码中捕捉从 MSIL 引发的异常](../dotnet/how-to-catch-exceptions-in-native-code-thrown-from-msil.md)<br/>
讨论如何捕获本机代码中的 CLR 和 C++ 异常。

[如何：定义和安装全局异常处理程序](../dotnet/how-to-define-and-install-a-global-exception-handler.md)<br/>
演示如何捕获所有未经处理的异常。

## <a name="related-sections"></a>相关章节

[异常处理](../cpp/exception-handling-in-visual-cpp.md)<br/>
介绍了标准 c + + 中的异常处理。

## <a name="see-also"></a>请参阅

[适用于.NET 和 UWP 组件扩展](../windows/component-extensions-for-runtime-platforms.md)