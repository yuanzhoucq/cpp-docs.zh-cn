---
title: "如何：使用 WRL 激活和使用 Windows 运行时组件 | Microsoft Docs"
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
ms.assetid: 54828f02-6af3-45d1-b965-d0104442f8d5
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 WRL 激活和使用 Windows 运行时组件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

文档演示如何使用[!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)]\([!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]\)初始化[!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]以及激活和使用[!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]组件。  
  
> [!NOTE]
>  此示例状态内置 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 组件。  若要了解如何创建自己可以以类似方式激活的组件，请参见 [演练：创建基本 Windows 运行时组件](../windows/walkthrough-creating-a-basic-windows-runtime-component-using-wrl.md)。  
  
 为了使用组件，您必须获取接口指针到该组件实现的类型。  此外，因为 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 的基础技术是组件对象模型 \(COM\) \(COM\)，则必须遵循 COM 规则维护类型的实例。  例如，您确定必须维护的 *引用数* 类型时从内存删除。  
  
 若要简化使用 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]，则 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 提供的聪明指针模板，[ComPtr\<T\>](../windows/comptr-class.md)，自动执行引用计数。  在声明变量时，指定 `ComPtr<`*interface\-name*`>` *identifier*。  若要访问接口成员中，适用于箭头成员访问运算符 \(`->`标识符。\)  
  
> [!IMPORTANT]
>  在调用接口函数时，始终要测试 `HRESULT` 返回值。  
  
## 激活和使用 Windows 运行时组件  
 以下步骤使用 `Windows::Foundation::IUriRuntimeClass` 接口演示如何创建 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 组件的一个活动，工厂创建该组件实例，并检索属性值。  这些示例还显示如何初始化 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]。  下面是完整的示例。  
  
> [!IMPORTANT]
>  尽管可以在 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 应用通常使用 [!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]，此示例使用图的控制台应用。  函数 \(如 `wprintf_s` \) 从 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 应用不可用。  有关在 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 应用中使用和函数的类型的更多信息，请参见 [CRT 函数不支持与 \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx) 和 [Win32 和 COM 中存储应用的](http://msdn.microsoft.com/library/windows/apps/br205757.aspx)。  
  
#### 激活和使用 Windows 运行时组件  
  
1.  包括 \(`#include`\) 任何必需的 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]、[!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)] 或标准 C\+\+ 库标头。  
  
     [!CODE [wrl-consume-component#2](../CodeSnippet/VS_Snippets_Misc/wrl-consume-component#2)]  
  
     我们建议您在 .cpp 文件中使用 `using namespace` 指令使代码更具可读性。  
  
2.  初始化应用执行的线程。  每个应用必须初始化其线程和线程模型。  此示例使用 [Microsoft::WRL::Wrappers::RoInitializeWrapper](../windows/roinitializewrapper-class.md) 类初始化 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 并指定 [RO\_INIT\_MULTITHREADED](http://msdn.microsoft.com/library/windows/apps/br224661.aspx) 为线程模型。  当销毁时，`RoInitializeWrapper` 类在构造调用 `Windows::Foundation::Initialize` 和 `Windows::Foundation::Uninitialize` 方法。  
  
     [!CODE [wrl-consume-component#3](../CodeSnippet/VS_Snippets_Misc/wrl-consume-component#3)]  
  
     在第二个语句，[RoInitializeWrapper::HRESULT](../windows/roinitializewrapper-hresult-parens-operator.md) 运算符返回从调用的 `HRESULT` 设置为 `Windows::Foundation::Initialize`。  
  
3.  创建 `ABI::Windows::Foundation::IUriRuntimeClassFactory` 接口的一个活动 *activation factory* 工厂。  
  
     [!CODE [wrl-consume-component#4](../CodeSnippet/VS_Snippets_Misc/wrl-consume-component#4)]  
  
     [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 使用完全限定的名称标识一类型。  `RuntimeClass_Windows_Foundation_Uri` 参数是包含 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 提供并需的运行时类名称的字符串。  
  
4.  初始化表示 URI `"http://www.microsoft.com"`的变量。[Microsoft::WRL::Wrappers::HString](../windows/hstring-class.md)  
  
     [!CODE [wrl-consume-component#6](../CodeSnippet/VS_Snippets_Misc/wrl-consume-component#6)]  
  
     在 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]中，不将 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 的字符串的内存。  相反，[!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 创建字符串的副本。为操作维护和使用的缓冲区\)，然后返回该句柄创建的缓冲区。  
  
5.  使用 `IUriRuntimeClassFactory::CreateUri` 工厂方法可创建 `ABI::Windows::Foundation::IUriRuntimeClass` 对象。  
  
     [!CODE [wrl-consume-component#7](../CodeSnippet/VS_Snippets_Misc/wrl-consume-component#7)]  
  
6.  调用 `IUriRuntimeClass::get_Domain` 方法以检索 `Domain` 属性的值。  
  
     [!CODE [wrl-consume-component#8](../CodeSnippet/VS_Snippets_Misc/wrl-consume-component#8)]  
  
7.  打印到域名控制台并返回。  所有 `ComPtr` 和 RAII 对象都离开范围并自动释放。  
  
     [!CODE [wrl-consume-component#9](../CodeSnippet/VS_Snippets_Misc/wrl-consume-component#9)]  
  
     [WindowsGetStringRawBuffer](http://msdn.microsoft.com/library/windows/apps/br224636.aspx) 函数检索 URI 基础 Unicode 字符串的窗体。  
  
 这是完整示例  
  
 [!CODE [wrl-consume-component#1](../CodeSnippet/VS_Snippets_Misc/wrl-consume-component#1)]  
  
## 编译代码  
 若要编译代码，请复制代码并将其粘贴到  项目中或一个名为 parallel\-matrix\-multiply.cpp 的文件中，然后在命令提示符窗口中运行以下命令。  
  
 **cl.exe wrl\-consume\-component.cpp runtimeobject.lib**  
  
## 请参阅  
 [Windows 运行时 C\+\+ 模板库 \(WRL\)](../windows/windows-runtime-cpp-template-library-wrl.md)