---
title: "CDialogImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDialogImpl"
  - "ATL.CDialogImpl"
  - "ATL::CDialogImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDialogImpl class"
  - "对话框, ATL"
ms.assetid: d430bc7b-8a28-4ad3-9507-277bdd2c2c2e
caps.latest.revision: 25
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDialogImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类为创建模式或无模式对话框的方法。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template <  
class T,  
class TBase= CWindow   
>  
class ATL_NO_VTABLE CDialogImpl :  
public CDialogImplBaseT< TBase>  
```  
  
#### 参数  
 `T`  
 您的选件类，从派生 `CDialogImpl`。  
  
 *TBase*  
 将新选件类基类。  默认基类是 [CWindow](../../atl/reference/cwindow-class.md)。  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[Create](../Topic/CDialogImpl::Create.md)|创建无模式对话框。|  
|[DestroyWindow](../Topic/CDialogImpl::DestroyWindow.md)|销毁无模式对话框。|  
|[DoModal](../Topic/CDialogImpl::DoModal.md)|创建一个模式对话框。|  
|[EndDialog](../Topic/CDialogImpl::EndDialog.md)|销毁一个模式对话框。|  
  
### CDialogImplBaseT方法  
  
|||  
|-|-|  
|[GetDialogProc](../Topic/CDialogImpl::GetDialogProc.md)|返回当前对话框过程。|  
|[MapDialogRect](../Topic/CDialogImpl::MapDialogRect.md)|映射该指定矩形的对话框单元以便屏幕单元\(像素为单位）。|  
|[OnFinalMessage](../Topic/CDialogImpl::OnFinalMessage.md)|调用接收最后一条消息后，通常 `WM_NCDESTROY`。|  
  
### 静态函数  
  
|||  
|-|-|  
|[DialogProc](../Topic/CDialogImpl::DialogProc.md)|处理发送到对话框。|  
|[StartDialogProc](../Topic/CDialogImpl::StartDialogProc.md)|调用，当第一个接收消息处理发送到对话框。|  
  
## 备注  
 `CDialogImpl` 可以创建模式或无模式对话框。  `CDialogImpl` 对话框提供程序，则使用默认消息映射处理消息的适当处理程序。  
  
 基类析构函数 **~CWindowImplRoot** 确保窗口在销毁对象之前会丢失。  
  
 `CDialogImpl` 从 **CDialogImplBaseT**派生，从 **CWindowImplRoot**而后者派生。  
  
> [!NOTE]
>  您的选件类必须定义指定对话框模板资源ID.的 **IDD** 成员  例如，ATL项目向导自动将以下行添加到您的选件类:  
  
 [!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/CPP/cdialogimpl-class_1.h)]  
  
 其中 `MyDlg` 是在向导的页 **名称** 输入的 **Short name**。  
  
|有关以下内容的更多信息|请参见|  
|-----------------|---------|  
|创建控件|[ATL教程](../../atl/active-template-library-atl-tutorial.md)|  
|使用在ATL的对话框|[ATL窗口选件类](../../atl/atl-window-classes.md)|  
|ATL项目向导|[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)|  
|对话框|[对话框](http://msdn.microsoft.com/library/windows/desktop/ms632588) 及随后的主题。[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]|  
  
## 要求  
 **Header:** atlwin.h  
  
## 请参阅  
 [BEGIN\_MSG\_MAP](../Topic/BEGIN_MSG_MAP.md)   
 [Class Overview](../../atl/atl-class-overview.md)