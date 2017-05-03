---
title: "静态库 (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "02/03/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
caps.latest.revision: 10
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 10
---
# 静态库 (C++/CX)
[!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]应用程序中使用的静态库可包含符合 ISO 标准的 C\+\+ 代码（包括 STL 类型），同时还调用 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]应用程序平台中未排除的 Win32 API。 静态库使用 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]组件，而且可以在一些限制下创建 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]组件。  
  
## 创建静态库  
  
#### 创建用于 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]应用程序的静态库  
  
1.  在菜单栏上，为 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)] 应用选择“文件”\>“新建”\>“项目”\>“空白静态库”。  
  
2.  在“解决方案资源管理器”中，打开项目的快捷菜单，然后选择“属性”。 在**“属性”**对话框中的**“配置属性”** **“常规”**页面上，将“ [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]应用程序支持”设置为**“是”**。  
  
3.  在“配置属性”\>“C\/C\+\+”页面上，将“使用 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 扩展”设置为“是\(\/ZW\)”。  
  
 编译新的静态库时，如果调用 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]应用排除的 Win32 API，编译器将引发错误 C3861“找不到标识符”。 若要查找 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]所支持的替代方法，请参见 [Alternatives to Windows APIs in Windows Store apps](http://msdn.microsoft.com/zh-cn/75568012-61e0-41cc-a4df-c698f54f21ec)。  
  
 如果将 C\+\+ 静态库项目添加到 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]应用程序解决方案，则可能必须更新该库项目的属性设置，以便将 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]支持属性设置为**“是”**。 无此设置代码也能生成和链接，但是当您尝试为 [!INCLUDE[win8_appstore_long](../cppcx/includes/win8-appstore-long-md.md)]验证该应用程序时，会发生错误。 编译静态库时的编译器设置应与使用该库的项目的编译器设置相同。  
  
 如果使用创建公共 `ref` 类、公共接口类或公共值类的静态库，则链接器会引发此警告：  
  
> **warning LNK4264:** 正在将使用 \/ZW 编译的对象文件归档到静态库中；请注意，创作 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]类型时，建议不要与包含 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]元数据的静态库链接  
  
 仅当静态库不生成在库自身之外被使用的 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]组件时，才能放心忽略此警告。 如果该库不使用其定义的组件，则链接器可通过优化去除实现，即使公共元数据包含类型信息，情况也不例外。 这意味着，静态库中的公共组件将进行编译，但不会在运行时激活。 因此，供其他组件或应用程序使用的任何 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]组件都必须以动态链接库 \(DLL\) 的形式实现。  
  
## 请参阅  
 [线程处理和封送处理](../cppcx/threading-and-marshaling-c-cx.md)