---
title: "CMyProviderCommand (MyProviderRS.H) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cmyprovidercommand
- myproviderrs.h
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderCommand class in MyProviderRS.H
ms.assetid: b30b956e-cc91-4cf5-9fe6-f8b1ce9cc2a5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fe0852b619dc89df4ab9a04f2e7dcbac5d308fce
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="cmyprovidercommand-myproviderrsh"></a>CMyProviderCommand (MyProviderRS.H)
`CMyProviderCommand`类是提供程序命令对象的实现。 它提供的实现`IAccessor`， `ICommandText`，和**ICommandProperties**接口。 `IAccessor`接口是在行集中的一个相同。 命令对象使用访问器来指定参数的绑定。 行集对象使用它们来指定输出列的绑定。 `ICommandText`接口是一种以文本上指定的命令。 此示例使用`ICommandText`接口更高版本时它将添加自定义代码; 它还将重写`ICommand::Execute`方法。 **ICommandProperties**接口处理所有的命令和行集对象的属性。  
  
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
  
 `IAccessor`接口管理所有命令和行集合中使用的绑定。 使用者调用**IAccessor::CreateAccessor**使用数组**DBBINDING**结构。 每个**DBBINDING**结构包含有关应如何处理列绑定 （如类型和长度） 的信息。 提供程序接收这些结构，然后确定应如何传输数据和是否需要任何转换。 `IAccessor`接口用于命令对象中，若要处理在命令中的任何参数。  
  
 命令对象还提供的实现`IColumnsInfo`。 OLE DB 需要`IColumnsInfo`接口。 此接口可以在命令中检索有关参数的信息的使用者。 行集对象使用`IColumnsInfo`接口以返回到提供程序的输出列的信息。  
  
 提供程序还包含一个接口，称为`IObjectWithSite`。 `IObjectWithSite`接口在 ATL 2.0 中实现，并允许实施者将自身的相关信息传递给其子级。 命令对象使用`IObjectWithSite`信息通知任何生成行集对象是谁创建它们。  
  
## <a name="see-also"></a>请参阅  
 [提供程序向导生成的文件](../../data/oledb/provider-wizard-generated-files.md)