---
title: 如何： 直接实例化 WRL 组件 |Microsoft 文档
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
ms.openlocfilehash: 127a8430e79e7963ea94646f70179df2f30450ff
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="how-to-instantiate-wrl-components-directly"></a>如何：直接实例化 WRL 组件
了解如何使用 Windows 运行时 c + + 模板库 (WRL)[Microsoft::WRL::Make](../windows/make-function.md)和[Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md)函数来实例化的模块中的组件，将其定义。  
  
 方法是直接实例化组件，你可以减少开销时，不需要类工厂或其他机制。 可以实例化直接在这两个通用 Windows 平台应用程序和桌面应用中的组件。  
  
若要了解如何使用 Windows 运行时 c + + 模板库创建传统型 COM 组件和其从外部的桌面应用程序进行实例化，请参阅[如何： 创建传统型 COM 组件](../windows/how-to-create-a-classic-com-component-using-wrl.md)。  
  
 本文档显示两个示例。 第一个示例使用`Make`函数来实例化组件。 第二个示例使用`MakeAndInitialize`函数来实例化可能会在构造过程中失败的组件。 (因为 COM 通常使用`HRESULT`值，而不是异常来指示错误，COM 类型通常不会引发从其构造函数。 `MakeAndInitialize` 使组件能够验证通过其构造参数`RuntimeClassInitialize`方法。)这两个示例定义一个基本的记录器接口，并通过定义将消息写入控制台的类中实现该接口。  
  
> [!IMPORTANT]
>  不能使用`new`运算符来实例化 Windows 运行时 c + + 模板库组件。 因此，我们建议您始终使用`Make`或`MakeAndInitialize`以直接实例化组件。  
  
### <a name="to-create-and-instantiate-a-basic-logger-component"></a>若要创建和实例化基本记录器组件  
  
1.  在 Visual Studio 中，创建**Win32 控制台应用程序**项目。 该项目命名，例如， `WRLLogger`。  
  
2.  添加**Midl 文件 (.idl)** 到项目文件，命名该文件`ILogger.idl`，然后添加以下代码：  
  
     [!code-cpp[wrl-logger-make#1](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_1.idl)]  
  
3.  使用下面的代码替换 WRLLogger.cpp 的内容。  
  
     [!code-cpp[wrl-logger-make#2](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_2.cpp)]  
  
### <a name="to-handle-construction-failure-for-the-basic-logger-component"></a>若要处理的基本记录器组件的构造失败  
  
1.  使用下面的代码的定义替换`CConsoleWriter`类。 此版本包含私有 string 成员变量，并重写`RuntimeClass::RuntimeClassInitialize`方法。 `RuntimeClassInitialize` 如果将失败的调用`SHStrDup`失败。  
  
     [!code-cpp[wrl-logger-makeandinitialize#1](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_3.cpp)]  
  
2.  使用下面的代码的定义替换`wmain`。 此版本使用`MakeAndInitialize`来实例化`CConsoleWriter`对象和检查`HRESULT`结果。  
  
     [!code-cpp[wrl-logger-makeandinitialize#2](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_4.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [Windows 运行时 c + + 模板库 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)   
 [Microsoft::WRL::Make](../windows/make-function.md)   
 [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md)