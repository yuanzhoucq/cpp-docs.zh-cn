---
title: "CSnapInItemImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSnapInItemImpl"
  - "ATL.CSnapInItemImpl"
  - "ATL::CSnapInItemImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSnapInItemImpl class"
  - "snap-ins"
  - "snap-ins, ATL support for"
  - "snap-ins, data items"
ms.assetid: 52caefbd-9eae-49b0-add2-d55524271aa7
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSnapInItemImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类为实现管理单元节点对象的方法。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template <  
class T,  
BOOL bIsExtension= FALSE  
>  
class ATL_NO_VTABLE CSnapInItemImpl :  
public CSnapInItem  
```  
  
#### 参数  
 `T`  
 您的选件类，从派生 `CSnapInItemImpl`。  
  
 *bIsExtension*  
 **TRUE**，如果对象是管理单元扩展名;否则 **FALSE**。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CSnapInItemImpl::CSnapInItemImpl](../Topic/CSnapInItemImpl::CSnapInItemImpl.md)|构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CSnapInItemImpl::AddMenuItems](../Topic/CSnapInItemImpl::AddMenuItems.md)|将菜单项添加到上下文菜单。|  
|[CSnapInItemImpl::Command](../Topic/CSnapInItemImpl::Command.md)|调用控制台，当自定义菜单项被选中。|  
|[CSnapInItemImpl::CreatePropertyPages](../Topic/CSnapInItemImpl::CreatePropertyPages.md)|添加页面、管理单元的属性表。|  
|[CSnapInItemImpl::FillData](../Topic/CSnapInItemImpl::FillData.md)|复制有关管理单元对象的信息到指定的流。|  
|[CSnapInItemImpl::GetResultPaneInfo](../Topic/CSnapInItemImpl::GetResultPaneInfo.md)|检索管理单元的 **RESULTDATAITEM** 结构。|  
|[CSnapInItemImpl::GetResultViewType](../Topic/CSnapInItemImpl::GetResultViewType.md)|确定结果窗格使用的视图的类型。|  
|[CSnapInItemImpl::GetScopePaneInfo](../Topic/CSnapInItemImpl::GetScopePaneInfo.md)|检索管理单元的 **SCOPEDATAITEM** 结构。|  
|[CSnapInItemImpl::Notify](../Topic/CSnapInItemImpl::Notify.md)|调用控制台通知用户执行的操作管理单元。|  
|[CSnapInItemImpl::QueryPagesFor](../Topic/CSnapInItemImpl::QueryPagesFor.md)|调用查看管理单元节点是否支持属性页。|  
|[CSnapInItemImpl::SetMenuInsertionFlags](../Topic/CSnapInItemImpl::SetMenuInsertionFlags.md)|修改管理单元对象的菜单插入标志。|  
|[CSnapInItemImpl::SetToolbarButtonInfo](../Topic/CSnapInItemImpl::SetToolbarButtonInfo.md)|设置指定的工具栏按钮的信息。|  
|[CSnapInItemImpl::UpdateMenuState](../Topic/CSnapInItemImpl::UpdateMenuState.md)|更新上下文菜单项的状态。|  
|[CSnapInItemImpl::UpdateToolbarButton](../Topic/CSnapInItemImpl::UpdateToolbarButton.md)|更新指定的工具栏按钮的状态。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CSnapInItemImpl::m\_bstrDisplayName](../Topic/CSnapInItemImpl::m_bstrDisplayName.md)|管理单元对象的名称。|  
|[CSnapInItemImpl::m\_resultDataItem](../Topic/CSnapInItemImpl::m_resultDataItem.md)|`CSnapInItemImpl` 对象使用的Windows **RESULTDATAITEM** 结构。|  
|[CSnapInItemImpl::m\_scopeDataItem](../Topic/CSnapInItemImpl::m_scopeDataItem.md)|`CSnapInItemImpl` 对象使用的Windows **SCOPEDATAITEM** 结构。|  
  
## 备注  
 `CSnapInItemImpl` 为托管格节点对象提供了一个基本的实现，例如添加菜单项和工具栏，并且，转发管理单元节点的命令将适当的处理过程正常工作。  使用几种不同的接口和映射类型，这些函数实现。  默认实现处理通知发送到节点对象是通过确定派生类的正确的实例然后转发消息到正确的实例。  
  
## 继承层次结构  
 `CSnapInItem`  
  
 `CSnapInItemImpl`  
  
## 要求  
 **Header:** atlsnap.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)