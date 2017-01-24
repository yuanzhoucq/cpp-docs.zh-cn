---
title: "关于异常的疑难解答：System.Runtime.InteropServices.COMException | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHCOM"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "COMException 类"
ms.assetid: 14b6de51-e039-4db7-9321-06c9e16e328a
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Runtime.InteropServices.COMException
当 COM 方法调用返回一个无法识别的 HRESULT 时，将引发 <xref:System.Runtime.InteropServices.COMException> 异常。  
  
## 相关提示  
 **检查该异常的 ErrorCode 属性，以确定 COM 对象返回的 HRESULT**  
 当运行时遇到不熟悉的 HRESULT 时，会引发 <xref:System.Runtime.InteropServices.COMException> 异常，该异常包含一个公共的 `ErrorCode` 属性，其中含有调用所返回的 HRESULT。 如果运行时有可用错误信息，则将相应信息返回调用方。 但是，如果 COM 组件开发人员未能包含错误信息，则运行时返回八位数的 HRESULT 代替消息字符串。 拥有 HRESULT 使调用方能够确定异常的原因。 有关更多信息，请参见[如何：映射 HRESULT 和异常](../Topic/How%20to:%20Map%20HRESULTs%20and%20Exceptions.md)。  
  
 **禁用承载进程。**  
 COM 用于在 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 和宿主进程之间进行通信。 因为它是在代码运行前使用的，所以调用 `CoInitializeSecurity` 将引发此异常。  
  
### 备注  
 公共语言运行时 \(CLR\) 将已知的 HRESULTS 转换成 .NET 异常，这使 COM 对象能够将有意义的错误信息返回托管客户端。 HRESULTS 到异常的映射还可以反向工作，即将特定的 HRESULT 返回到非托管客户端。  
  
 将后期绑定参数传递给 Microsoft Office 对象的方法以后，如果这些对象是 COM 对象，则可能引发 <xref:System.Runtime.InteropServices.COMException> 异常。 后期联编程序假定：此类方法调用涉及 `ByRef` 参数，并且所传递的属性具有 `Set` 访问器。 如果相应属性不具有该访问器，则 [!INCLUDE[dnprdnshort](../Token/dnprdnshort_md.md)] 生成一个 <xref:System.MissingMethodException> 异常 \(HRESULT CORE\_E\_MISSINGMETHOD\)。 要处理此行为，请使用早期绑定对象或传递变量而不是对象的属性。  
  
## 请参阅  
 <xref:System.Runtime.InteropServices.COMException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [处理 COM 互操作异常](../Topic/Handling%20COM%20Interop%20Exceptions.md)