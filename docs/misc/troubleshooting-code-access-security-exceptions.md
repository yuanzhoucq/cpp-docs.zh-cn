---
title: "关于代码访问安全性异常的疑难解答 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "CodeAccessPermission 类"
  - "CodeAccessSecurityException 类"
  - "代码访问安全, 疑难解答"
  - "安全性 [调试器], 代码访问安全疑难解答"
  - "代码访问安全疑难解答"
ms.assetid: ca368d3b-f6d0-4c89-af59-d94f343fca35
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于代码访问安全性异常的疑难解答
权限控制代码可以执行以及不可以执行哪些操作。 当应用程序执行时，运行时会赋予它一组权限。 如果应用程序具有足够的权限，它将正常运行；否则将发生安全异常。  
  
 赋予代码的权限是由启动应用程序的位置（如 Internet、Intranet 或本地计算机）以及运行应用程序的计算机上的安全设置确定的。 由于这些设置会因计算机而异，因此您无法始终预见代码是否会收到足够的权限。  
  
 如果本地计算机上的安全策略允许，则可以通过请求权限来确保代码能够执行。 如果不请求必要的权限，将面临代码无法执行的风险。 有关代码访问权限和请求这些权限的详细信息，请参阅[代码访问权限](http://msdn.microsoft.com/zh-cn/e5ae402f-6dda-4732-bbe8-77296630f675)或 [NIB：请求权限](http://msdn.microsoft.com/zh-cn/0447c49d-8cba-45e4-862c-ff0b59bebdc2)。 有关 `Try...Catch` 块的更多信息，请参阅 [Try...Catch...Finally 语句](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)。  
  
 如果需要，[!INCLUDE[ndptecclick](../ide/includes/ndptecclick_md.md)] 应用程序可以使用应用程序设计器中的安全页来请求附加权限。 有关详细信息，请参阅 [如何：设置 ClickOnce 应用程序的自定义权限](../Topic/How%20to:%20Set%20Custom%20Permissions%20for%20a%20ClickOnce%20Application.md)。  
  
 代码访问安全异常的可能原因包括：  
  
-   **剪贴板。**以编程方式从剪贴板粘贴是托管代码的一项受限功能，因为剪贴板可能包含敏感的信息。  
  
-   **注册表或文件系统访问。**对本地文件系统的访问是受限制的。 如果要访问随程序集部署的文件或资源，请使用代码 `Assembly.GetExecutingAssembly.Location` 来获取程序集的路径。  
  
-   **网络访问。**请确保您的程序集使用的协议与加载程序集所使用的协议相同。 通常，仅允许与作为程序集的源的 URL 进行网络通信。  
  
-   **打印。**在 Internet 区域中运行的软件只能通过使用通用对话框进行打印。如果它使用通用对话框来允许用户选择打印机，将被限制为只具有默认打印机使用权限。  
  
-   **序列化。**从任意数据重新生成对象的能力仅限于以完全信任运行的代码。 对于 XML 序列化，在技术上讲，`XmlSerializer` 类型应为部分受信任的代码使用。 有关 `XmlSerializer` 类型的更多信息，请参阅 [XmlSerializer 类](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx)。  
  
-   **反射。**运行时的与反射相关的许多功能禁止部分受信任的代码使用。  
  
## 测试代码以确定它是否会引发代码访问安全异常  
 如果您的代码块有可能引发 `CodeAccessSecurityException`，使用 `Try...Catch` 块可以让代码在能够执行时执行，在无法执行时避免失败。  
  
 有时，可能需要将应用程序设计为根据主机系统赋予它的权限来调整自己的行为。 例如，您可能需要在应用程序没有打印权限时禁用菜单上的“打印”命令。  
  
 要进行这方面的测试，可以创建一个从 `CodeAccessPermission` 派生的类（如 `FileIOPermission`）的实例。 然后，可以在 `Demand` 块的内部针对该权限执行 `Try...Catch` 方法。 如果引发了异常，则说明程序集不具备该权限。  
  
 下面的示例测试程序集是否具有 `EventLogPermission` 权限，方法是执行或创建一个 `EventLogPermission`，并在 `Demand` 块内执行其 `Try...Catch` 方法，以确定 `Demand` 是否成功。  
  
```  
Try Dim MyPermission As New EventLogPermission MyPermission.Demand() MsgBox(MyPermission.ToString()) Catch ex As Exception MsgBox("Assembly lacks EventLogPermission.") End Try  
```  
  
## 请参阅  
 [代码访问权限](http://msdn.microsoft.com/zh-cn/e5ae402f-6dda-4732-bbe8-77296630f675)   
 [NIB：请求权限](http://msdn.microsoft.com/zh-cn/0447c49d-8cba-45e4-862c-ff0b59bebdc2)   
 [代码访问安全性基础知识](../Topic/Code%20Access%20Security%20Basics.md)