---
title: "如何：直接实例化 WRL 组件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: 1a9fa011-0cee-4abf-bf83-49adf53ff906
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：直接实例化 WRL 组件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

了解如何使用 [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] \([!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]\)[Microsoft::WRL::Make](../windows/make-function.md)和[Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md)函数去实例化定义的模块组件。  
  
 当您不需要类工厂或其他机制时，通过直接实例化组件可以降低开销。  可以直接在[!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)]应用程序和在桌面应用程序中实例化一个组件。  
  
 若要了解如何使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 创建一个基本的 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 组件并将其从外部 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 应用程序实例化，请参见 [演练：创建基本 Windows 运行时组件](../windows/walkthrough-creating-a-basic-windows-runtime-component-using-wrl.md)。  若要了解如何使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 创建一个基本的COM组件并将其从外部桌面应用程序实例化，请参见[如何：创建传统型 COM 组件](../windows/how-to-create-a-classic-com-component-using-wrl.md) 。  
  
 此文档显示两个示例。  第一个示例使用 `Make` 函数实例化组件。  第二个示例使用 `MakeAndInitialize` 函数实例化构造失败的组件。\(由于 COM 通常使用 `HRESULT` 值，而不是异常，为了指示错误，COM 类型通常不从其构造函数抛出。  `MakeAndInitialize` 通过 `RuntimeClassInitialize` 方法使组件验证其构造实参。\)两个示例定义一个基本的记录器接口并通过定义写消息到控制台的类来实现该接口。  
  
> [!IMPORTANT]
>  不能使用 `new` 运算符实例化 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]组件。  因此，建议您始终使用 `Make` 或 `MakeAndInitialize` 直接实例化组件。  
  
### 创建和实例化一个基本的记录器组件  
  
1.  在 Visual Studio 中，创建一个**Win32控制台应用程序**项目。  例如，将项目命名为`WRLLogger`。  
  
2.  添加一个**Midl File \(.idl\)**文件到项目，将文件命名为 `ILogger.idl`，然后添加以下代码：  
  
     [!CODE [wrl-logger-make#1](../CodeSnippet/VS_Snippets_Misc/wrl-logger-make#1)]  
  
3.  使用以下代码替换“WRLLogger.cpp”的内容：  
  
     [!CODE [wrl-logger-make#2](../CodeSnippet/VS_Snippets_Misc/wrl-logger-make#2)]  
  
### 处理基本的记录器组件的构造失败事件  
  
1.  用下面的代码替换 `CConsoleWriter` 类的定义。  此版本包含一个私有字符串成员变量并重写 `RuntimeClass::RuntimeClassInitialize` 方法。  如果对 `SHStrDup` 的调用失败，则`RuntimeClassInitialize` 失败。  
  
     [!code-cpp[wrl-logger-makeandinitialize#1](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_1.cpp)]  
  
2.  用下面的代码替换方法`wmain`的定义。  此版本使用 `MakeAndInitialize` 实例化 `CConsoleWriter` 对象和检查 `HRESULT` 结果。  
  
     [!code-cpp[wrl-logger-makeandinitialize#2](../windows/codesnippet/CPP/how-to-instantiate-wrl-components-directly_2.cpp)]  
  
## 请参阅  
 [Windows 运行时 C\+\+ 模板库 \(WRL\)](../windows/windows-runtime-cpp-template-library-wrl.md)   
 [Microsoft::WRL::Make](../windows/make-function.md)   
 [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md)