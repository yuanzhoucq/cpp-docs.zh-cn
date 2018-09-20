---
title: 如何： 直接实例化 WRL 组件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 1a9fa011-0cee-4abf-bf83-49adf53ff906
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d0c0ea8537922c2458a48adf5a086dfec4b992f5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381097"
---
# <a name="how-to-instantiate-wrl-components-directly"></a>如何：直接实例化 WRL 组件

了解如何使用 Windows 运行时 c + + 模板库 (WRL)[Microsoft::WRL::Make](../windows/make-function.md)并[Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md)函数来实例化组件的模块中的将其定义。

通过直接实例化组件，您可以减少开销时，不需要类工厂或其他机制。 您可以实例化组件直接在这两个通用 Windows 平台应用和桌面应用中。

若要了解如何使用 Windows 运行时 c + + 模板库创建传统型 COM 组件并将其实例从外部桌面应用程序，请参阅[如何： 创建传统型 COM 组件](../windows/how-to-create-a-classic-com-component-using-wrl.md)。

本文档演示两个示例。 第一个示例使用`Make`函数来实例化组件。 第二个示例使用`MakeAndInitialize`函数来实例化一个组件，它在构造期间可能会失败。 （由于 COM 通常使用而不是异常的 HRESULT 值，以指示错误，COM 类型通常不会引发从其构造函数。 `MakeAndInitialize` 使组件可以验证通过其构造参数`RuntimeClassInitialize`方法。)这两个示例定义基本记录器接口，并通过定义向控制台写入消息的类中实现该接口。

> [!IMPORTANT]
> 不能使用**新**运算符来实例化 Windows 运行时 c + + 模板库组件。 因此，我们建议始终使用`Make`或`MakeAndInitialize`直接实例化组件。

### <a name="to-create-and-instantiate-a-basic-logger-component"></a>若要创建并实例化一个基本的记录器组件

1. 在 Visual Studio 中创建**Win32 控制台应用程序**项目。 该项目命名，例如， *WRLLogger*。

2. 添加**Midl 文件 (.idl)** 到项目文件中，将文件命名`ILogger.idl`，然后添加以下代码：

   [!code-cpp[wrl-logger-make#1](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_1.idl)]

3. 使用下面的代码的内容替换为`WRLLogger.cpp`。

   [!code-cpp[wrl-logger-make#2](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_2.cpp)]

### <a name="to-handle-construction-failure-for-the-basic-logger-component"></a>若要处理的基本记录器组件的构造故障

1. 使用以下代码替换的定义`CConsoleWriter`类。 此版本包含私有字符串成员变量和重写`RuntimeClass::RuntimeClassInitialize`方法。 `RuntimeClassInitialize` 如果失败的调用`SHStrDup`失败。

   [!code-cpp[wrl-logger-makeandinitialize#1](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_3.cpp)]

2. 使用以下代码替换的定义`wmain`。 此版本使用`MakeAndInitialize`若要实例化`CConsoleWriter`对象，并检查 HRESULT 结果。

   [!code-cpp[wrl-logger-makeandinitialize#2](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_4.cpp)]

## <a name="see-also"></a>请参阅

[Windows 运行时 C++ 模板库 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)<br/>
[Microsoft::WRL::Make](../windows/make-function.md)<br/>
[Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md)