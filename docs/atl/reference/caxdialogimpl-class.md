---
title: "CAxDialogImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CAxDialogImpl"
  - "ATL.CAxDialogImpl"
  - "CAxDialogImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, 对话框"
  - "CAxDialogImpl class"
ms.assetid: 817df483-3fa8-44e7-8487-72ba0881cd27
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CAxDialogImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类实现一个对话框\(模式或无模式\)承载ActiveX控件。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template <  
class T,  
class TBase= CWindow  
>  
class ATL_NO_VTABLE CAxDialogImpl :  
public CDialogImplBaseT< TBase>  
```  
  
#### 参数  
 `T`  
 您的选件类，从派生 `CAxDialogImpl`。  
  
 *TBase*  
 **CDialogImplBaseT**的基windows选件类。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAxDialogImpl::AdviseSinkMap](../Topic/CAxDialogImpl::AdviseSinkMap.md)|调用此方法建议或unadvise在对象接收器的映射事件映射的所有项。|  
|[CAxDialogImpl::Create](../Topic/CAxDialogImpl::Create.md)|调用此方法创建无模式对话框。|  
|[CAxDialogImpl::DestroyWindow](../Topic/CAxDialogImpl::DestroyWindow.md)|调用此方法销毁无模式对话框。|  
|[CAxDialogImpl::DoModal](../Topic/CAxDialogImpl::DoModal.md)|调用此方法将创建一个模式对话框。|  
|[CAxDialogImpl::EndDialog](../Topic/CAxDialogImpl::EndDialog.md)|调用此方法销毁一个模式对话框。|  
|[CAxDialogImpl::GetDialogProc](../Topic/CAxDialogImpl::GetDialogProc.md)|调用此方法获取指向 `DialogProc` 回调函数。|  
|[CAxDialogImpl::GetIDD](../Topic/CAxDialogImpl::GetIDD.md)|调用此方法获取对话框模板资源ID|  
|[CAxDialogImpl::IsDialogMessage](../Topic/CAxDialogImpl::IsDialogMessage.md)|调用此方法确定消息是否适用于此对话框使用，则为;如果是，处理消息。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CAxDialogImpl::m\_bModal](../Topic/CAxDialogImpl::m_bModal.md)|仅存在于变量调试版本和设置为true，如果对话框是模式。|  
  
## 备注  
 `CAxDialogImpl` 允许您创建模式或无模式对话框。  `CAxDialogImpl` 对话框提供程序，则使用默认消息映射处理消息的适当处理程序。  
  
 `CAxDialogImpl` 从 `CDialogImplBaseT`派生，从 *TBase* \(默认情况下，`CWindow`\)和 `CMessageMap`而后者派生。  
  
 您的选件类必须定义指定对话框模板资源ID.的IDD成员  例如，将使用 **添加选件类** 对话框中ATL对话框对象自动将以下行添加到您的选件类:  
  
 [!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/CPP/caxdialogimpl-class_1.h)]  
  
 其中 `MyDialog` 是在ATL对话框向导输入的 **短名称**。  
  
 请参见 [实现对话框](../../atl/implementing-a-dialog-box.md) 有关更多信息。  
  
 请注意请在 `CAxDialogImpl` 创建的模式对话框的ActiveX控件将不支持快捷键。  使用您的消息循环，若要支持请在 `CAxDialogImpl`创建对话框的快捷键，请创建无模式对话框，因此，在使用消息从队列处理快捷键后使用 [CAxDialogImpl::IsDialogMessage](../Topic/CAxDialogImpl::IsDialogMessage.md)。  
  
 有关 `CAxDialogImpl`的更多信息，请参见 [ATL控件包容常见问题](../../atl/atl-control-containment-faq.md)。  
  
## 继承层次结构  
 [CMessageMap](../../atl/reference/cmessagemap-class.md)  
  
 `TBase`  
  
 `CWindowImplRoot`  
  
 `CDialogImplBaseT`  
  
 `CAxDialogImpl`  
  
## 要求  
 **Header:** atlwin.h  
  
## 请参阅  
 [CDialogImpl Class](../../atl/reference/cdialogimpl-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)