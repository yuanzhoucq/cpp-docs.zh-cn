---
title: "演练：使用 WRL 创建基本 Windows 运行时组件 | Microsoft Docs"
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
ms.assetid: 6e3f0986-7905-4f94-90e5-22c2ebfc8cd0
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 演练：使用 WRL 创建基本 Windows 运行时组件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文档演示如何使用 [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] ([!INCLUDE[cppwrl_short](../windows/includes/cppwrl_short_md.md)]) 创建基本 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 组件。 该组件将两个数相加，并引发事件时的结果是素数。 本文档还演示了如何通过使用组件 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 使用 JavaScript 的应用程序。  
  
## <a name="prerequisites"></a>先决条件  
  
-   它提供坚实基础 [Windows 运行时](http://msdn.microsoft.com/library/windows/apps/br211377.aspx)。  
  
-   熟悉 COM。  
  
### <a name="to-create-a-basic-includewrttokenwrtmdmd-component-that-adds-two-numbers"></a>若要创建一个基本 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 两个数相加的组件  
  
1.  在 Visual Studio 中创建 Visual c + + `WRLClassLibrary` 项目。 文档 [类库项目模板](../windows/wrl-class-library-project-template.md) 介绍如何下载此模板。 将项目命名为 `Contoso`。  
  
2.  在 Contoso.cpp 和 Contoso.idl 替换"WinRTClass"与"计算器"的所有实例。  
  
3.  在 Contoso.idl，添加 `Add` 方法 `ICalculator` 接口。  
  
     [!code-cpp[wrl-basic-component#1](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_1.idl)]  
  
4.  在 Contoso.cpp，添加 `Add` 方法 `public` 部分 `Calculator` 类。  
  
     [!code-cpp[wrl-basic-component#2](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_2.cpp)]  
  
    > [!IMPORTANT]
    >  因为您将创建一个 COM 组件，请记住使用 `__stdcall` 调用约定。  
  
     我们建议你使用 `_Out_` 和其他源代码批注语言 (SAL) 批注，以描述函数如何使用它的参数。 SAL 注释还描述返回值。 SAL 注释使用 [C/c + + 代码分析工具](../Topic/Code%20Analysis%20for%20C-C++%20Overview.md) 以发现可能存在的缺陷在 C 和 c + + 中的源代码。 该工具会报告的常见编码错误包括缓冲区溢出、 未初始化的内存、 null 指针取消引用和内存和资源泄漏。  
  
### <a name="to-use-the-component-from-a-includewin8appnamelongtokenwin8appnamelongmdmd-app-that-uses-javascript"></a>若要通过使用组件 [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] 使用 JavaScript 的应用程序  
  
1.  在 Visual Studio 中，添加新的 JavaScript `Blank App` 项目合并为 `Contoso` 解决方案。 将项目命名为 `CalculatorJS`。  
  
2.  在 `CalculatorJS` 项目中，添加对引用 `Contoso` 项目。  
  
3.  在 default.html，将 `body` 带有这些 UI 元素的节︰  
  
     [!code-html[wrl-basic-component#3](../windows/codesnippet/Html/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_3.html)]  
  
4.  在 default.js 中，实现 `OnClick` 函数。  
  
     [!code-javascript[wrl-basic-component#4](../windows/codesnippet/JavaScript/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_4.js)]  
  
    > [!NOTE]
    >  在 JavaScript 中，方法名称的第一个字母更改为小写，以匹配标准命名约定。  
  
### <a name="to-add-an-event-that-fires-when-a-prime-number-is-calculated"></a>若要添加计算质数时触发的事件  
  
1.  在 Contoso.idl 声明前 `ICalculator`, ，定义的委托类型， `PrimeNumberEvent`, ，该属性提供 `int` 参数。  
  
     [!code-cpp[wrl-basic-component#5](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_5.idl)]  
  
     当您使用 `delegate` 关键字，MIDL 编译器会创建一个包含接口 `Invoke` 与该委托签名匹配的方法。 在此示例中，所生成的文件 Contoso_h.h 定义 `IPrimeNumberEvent` 接口，此过程后面部分中使用该接口。  
  
     [!code-cpp[wrl-basic-component#13](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_6.cpp)]  
  
2.  在 `ICalculator` 接口中，定义 `PrimeNumberFound` 事件。  `eventadd` 和 `eventremove` 特性指定的使用者 `ICalculator` 接口可以同时订阅和取消订阅此事件。  
  
     [!code-cpp[wrl-basic-component#6](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_7.idl)]  
  
3.  在 Contoso.cpp，添加 `private` [Microsoft::WRL::EventSource](../windows/eventsource-class.md) 成员变量来管理事件订阅服务器和调用事件处理程序。  
  
     [!code-cpp[wrl-basic-component#7](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_8.cpp)]  
  
4.  在 Contoso.cpp，实现 `add_PrimeNumberFound` 和 `remove_PrimeNumberFound` 方法。  
  
     [!code-cpp[wrl-basic-component#8](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_9.cpp)]  
  
### <a name="to-raise-the-event-when-a-prime-number-is-calculated"></a>若要引发事件时计算素数  
  
1.  在 Contoso.cpp，添加 `IsPrime` 方法 `private` 部分 `Calculator` 类。  
  
     [!code-cpp[wrl-basic-component#12](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_10.cpp)]  
  
2.  修改 `Calculator`的 `Add` 方法来调用 [Microsoft::WRL::EventSource::InvokeAll](../windows/eventsource-invokeall-method.md) 方法计算质数时。  
  
     [!code-cpp[wrl-basic-component#11](../windows/codesnippet/CPP/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_11.cpp)]  
  
### <a name="to-handle-the-event-from-javascript"></a>从 JavaScript 对事件进行处理  
  
1.  在 default.html，修改 `body` 部分以包括包含质数文本区域。  
  
     [!code-html[wrl-basic-component#9](../windows/codesnippet/Html/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_12.html)]  
  
2.  在 default.js 中，修改 `Add` 函数来处理 `PrimeNumberFound` 事件。 事件处理程序将质数追加到由上一步定义的文本区域。  
  
     [!code-javascript[wrl-basic-component#10](../windows/codesnippet/JavaScript/walkthrough-creating-a-basic-windows-runtime-component-using-wrl_13.js)]  
  
    > [!NOTE]
    >  在 JavaScript 中，事件名称更改为小写，并以"on"以匹配标准命名约定预置。  
  
 下图显示基本计算器应用程序。  
  
 ![使用 JavaScript 的基本计算器应用程序](../windows/media/wrl_basic_component.png "WRL_Basic_Component")  
  
## <a name="next-steps"></a>后续步骤  
  
## <a name="see-also"></a>另请参阅  
 [Windows 运行时 c + + 模板库 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)   
 [类库项目模板](../windows/wrl-class-library-project-template.md)   
 [C/c + + 代码分析工具](../Topic/Code%20Analysis%20for%20C-C++%20Overview.md)