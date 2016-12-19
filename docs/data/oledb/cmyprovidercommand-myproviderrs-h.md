---
title: "CMyProviderCommand (MyProviderRS.H) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cmyprovidercommand"
  - ""myproviderrs.h""
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MyProviderRS.H 中的 CMyProviderCommand 类"
  - "OLE DB 提供程序, 向导生成的文件"
ms.assetid: b30b956e-cc91-4cf5-9fe6-f8b1ce9cc2a5
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMyProviderCommand (MyProviderRS.H)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMyProviderCommand` 类是提供程序命令对象的实现。  它提供 `IAccessor`、`ICommandText` 和 **ICommandProperties** 接口的实现。  `IAccessor` 接口与行集合中的接口相同。  命令对象使用访问器指定参数的绑定。  行集合对象使用它们指定输出列的绑定。  `ICommandText` 接口是以文本方式指定命令的有用方法。  此示例稍后在添加自定义代码时将使用 `ICommandText` 接口；它也将重写 `ICommand::Execute` 方法。  **ICommandProperties** 接口处理命令和行集合对象的所有属性。  
  
```  
// CMyProviderCommand  
class ATL_NO_VTABLE CMyProviderCommand :   
class ATL_NO_VTABLE CMyProviderCommand :   
   public CComObjectRootEx<CComSingleThreadModel>,  
   public IAccessorImpl<CMyProviderCommand>,  
   public ICommandTextImpl<CMyProviderCommand>,  
   public ICommandPropertiesImpl<CMyProviderCommand>,  
   public IObjectWithSiteImpl<CMyProviderCommand>,  
   public IConvertTypeImpl<CMyProviderCommand>,  
   public IColumnsInfoImpl<CMyProviderCommand>  
```  
  
 `IAccessor` 接口管理命令和行集合中使用的所有绑定。  使用者用 **DBBINDING** 结构数组调用 **IAccessor::CreateAccessor**。  每个 **DBBINDING** 结构都包含有关如何处理列绑定的信息（如类型和长度）。  提供程序接收结构，然后确定数据应该如何传输和是否需要转换。  `IAccessor` 接口在命令对象中用于处理命令中的任何参数。  
  
 命令对象还提供 `IColumnsInfo` 的实现。  OLE DB 要求 `IColumnsInfo` 接口。  该接口允许使用者检索命令中的参数信息。  行集合对象使用 `IColumnsInfo` 接口将有关输出列的信息返回给提供程序。  
  
 提供程序还包含一个称为 `IObjectWithSite` 的接口。  `IObjectWithSite` 接口在 ATL 2.0 中实现并使实施者得以将有关自身的信息传递给其子级。  命令对象使用 `IObjectWithSite` 信息通知任何生成的行集合对象是谁创建了它们。  
  
## 请参阅  
 [提供程序向导生成的文件](../../data/oledb/provider-wizard-generated-files.md)