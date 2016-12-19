---
title: "如何：使用 WRL 创建传统型 COM 组件 | Microsoft Docs"
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
ms.assetid: 5efe7690-90d5-4c3c-9e53-11a14cefcb19
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 WRL 创建传统型 COM 组件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可使用 [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] ([!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]) 来创建在桌面应用程序中使用的基本经典 COM 组件，也可以将其用于 [!INCLUDE[win8_appstore_long](../build/reference/includes/win8_appstore_long_md.md)] 应用程序。 用于创建 COM 组件时，[!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 需要的代码可能比 ATL 少。 有关 COM 的信息子集的 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 支持，请参阅 [Windows 运行时 c + + 模板库 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)。  
  
 本文档演示如何使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 来创建基本 COM 组件。 尽管可以使用最适合你需求的部署机制，本文档还会展示一种从桌面应用程序注册及使用 COM 组件的基本方法。  
  
### <a name="to-use-the-includecppwrlshorttokencppwrlshortmdmd-to-create-a-basic-classic-com-component"></a>使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 来创建基本经典 COM 组件  
  
1.  在 Visual Studio 中，创建 **空白解决方案** 项目。 该项目命名，例如， `WRLClassicCOM`。  
  
2.  添加 **Win32 项目** 到解决方案。 该项目命名，例如， `CalculatorComponent`。 在 **应用程序设置** 选项卡上，选择 **DLL**。  
  
3.  添加 **Midl 文件 (.idl)** 到项目文件。 例如，命名该文件， `CalculatorComponent.idl`。  
  
4.  将此代码添加到 CalculatorComponent.idl：  
  
     [!code-cpp[wrl-classic-com-component#1](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_1.idl)]  
  
5.  在 CalculatorComponent.cpp 中，定义 `CalculatorComponent` 类。  `CalculatorComponent` 类继承自 [Microsoft::WRL::RuntimeClass](../windows/runtimeclass-class.md)。 [Microsoft::WRL::RuntimeClassFlags \< ClassicCom>](../windows/runtimeclassflags-structure.md) 指定的类派生自 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509\(v=vs.85\).aspx) 和 not [IInspectable](http://msdn.microsoft.com/library/br205821\(v=vs.85\).aspx)。 (`IInspectable` 只适用于 [!INCLUDE[win8_appstore_short](../windows/includes/win8_appstore_short_md.md)] 应用程序组件。) `CoCreatableClass` 为可以如与函数一起使用的类创建一个工厂 [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615\(v=vs.85\).aspx)。  
  
     [!code-cpp[wrl-classic-com-component#2](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_2.cpp)]  
  
6.  用下面的代码替换 dllmain.cpp 的代码。 此文件定义 DLL 导出函数。 这些函数将使用 [Microsoft::WRL::Module](../windows/module-class.md) 类来管理该模块的类工厂。  
  
     [!code-cpp[wrl-classic-com-component#3](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_3.cpp)]  
  
7.  添加 **模块定义文件 (.def)** 到项目文件。 例如，命名该文件， `CalculatorComponent.def`。 此文件为链接器提供了要导出的函数的名称。  
  
8.  将此代码添加到 CalculatorComponent.def：  
  
     [!CODE [wrl-classic-com-component#4](../CodeSnippet/VS_Snippets_Misc/wrl-classic-com-component#4)]  
  
9. 将 runtimeobject.lib 添加到链接器行。 若要了解如何操作，请参阅 [。用作链接器输入 lib 文件](../build/reference/dot-lib-files-as-linker-input.md)。  
  
### <a name="to-consume-the-com-component-from-a-desktop-app"></a>从桌面应用程序使用 COM 组件  
  
1.  向 Windows 注册表注册 COM 组件。 若要执行此操作，创建注册表项文件，将其命名 `RegScript.reg`, ，并添加以下文本。 替换 *\< dll 路径 >* 与您的 DLL 的路径 — 例如， `C:\\temp\\WRLClassicCOM\\Debug\\CalculatorComponent.dll`。  
  
     [!CODE [wrl-classic-com-component#5](../CodeSnippet/VS_Snippets_Misc/wrl-classic-com-component#5)]  
  
2.  运行 RegScript.reg 或将其添加到你的项目的 **后期生成事件**。 有关详细信息，请参阅 [预生成事件/生成后事件命令行对话框](../Topic/Pre-build%20Event-Post-build%20Event%20Command%20Line%20Dialog%20Box.md)。  
  
3.  添加 **Win32 控制台应用程序** 到解决方案的项目。 该项目命名，例如， `Calculator`。  
  
4.  用此代码替换 Calculator.cpp 的内容：  
  
     [!code-cpp[wrl-classic-com-component#6](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_6.cpp)]  
  
## <a name="robust-programming"></a>可靠编程  
 本文档使用标准 COM 函数来演示可使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 来创建 COM 组件并使其可用于支持 COM 的任何技术。 您还可以使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 类型，如 [Microsoft::WRL::ComPtr](../windows/comptr-class.md) 在桌面应用程序来管理 COM 和其他对象的生存期。 下面的代码使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 来管理 `ICalculatorComponent` 指针的生存期。 `CoInitializeWrapper` 类是一种 RAII 包装，可保证 COM 库已释放，并保证 COM 库的生存期长于 `ComPtr` 智能指针对象。  
  
 [!code-cpp[wrl-classic-com-component#7](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_7.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [Windows 运行时 c + + 模板库 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)