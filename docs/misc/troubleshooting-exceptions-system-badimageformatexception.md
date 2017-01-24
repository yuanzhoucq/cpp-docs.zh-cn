---
title: "关于异常的疑难解答：System.BadImageFormatException | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "BadImageFormatException 类"
ms.assetid: 8d2b385a-3d6d-4dfa-8546-7ece562867e3
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.BadImageFormatException
当 DLL 或可执行程序的文件映像无效时，便会引发 <xref:System.BadImageFormatException> 异常。  
  
## 相关提示  
 **如果您的应用程序使用了 32 位组件，请确保该应用程序始终采用 32 位应用程序的运行方式。**  
 如果应用程序项目的**“平台目标”**属性设置为 `AnyCPU`，则编译后的应用程序在 64 位或 32 位模式中均可运行。 如果采用 64 位应用程序运行方式，则实时 \(JIT\) 编译器便会生成 64 位本机代码。 如果应用程序依赖于某个 32 位托管组件或非托管组件，则在 64 位模式中无法加载该组件。 若要纠正此问题，请将项目的**“平台目标”**属性设置为 `x86`，然后重新编译。  
  
 **确保未使用利用其他 .NET Framework 版本创建的组件。**  
 如果使用 [!INCLUDE[net_v10_short](../Token/net_v10_short_md.md)] 或 [!INCLUDE[net_v11_short](../misc/includes/net_v11_short_md.md)] 开发的应用程序或组件尝试加载使用 [!INCLUDE[net_v20SP1_short](../misc/includes/net_v20sp1_short_md.md)] 或更高版本开发的程序集，或者使用 [!INCLUDE[net_v20SP1_short](../misc/includes/net_v20sp1_short_md.md)] 或 [!INCLUDE[net_v35_short](../misc/includes/net_v35_short_md.md)] 开发的应用程序尝试加载使用 [!INCLUDE[net_v40_short](../misc/includes/net_v40_short_md.md)] 开发的程序集，便会引发此异常。<xref:System.BadImageFormatException> 异常可能会报告作为编译时错误，或在运行时可能会引发该异常。 有关示例，请参见 <xref:System.BadImageFormatException> 类。  
  
 **确保文件映像是有效的托管程序集或模块。**  
 当非托管动态链接库或可执行文件传递给 <xref:System.Reflection.Assembly.Load%2A> 方法进行加载时会引发此异常。  
  
 有关更多信息，Visual Basic 用户可参考[互操作性疑难解答](../Topic/Troubleshooting%20Interoperability%20\(Visual%20Basic\).md)。  
  
## 备注  
 对 C\+\+ 可执行文件进行反射可能会引发此异常。 这极有可能是因为 C\+\+ 编译器从可执行文件中剥离重定位地址或 .Reloc 节引起的。 若要在 C\+\+ 可执行文件中保留 .relocation 地址，请在链接时指定 **\/fixed:no**。  
  
 有关此异常的更多原因，请参见 <xref:System.BadImageFormatException> 类。  
  
## 请参阅  
 <xref:System.BadImageFormatException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)