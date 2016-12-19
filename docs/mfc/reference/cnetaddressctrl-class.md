---
title: "CNetAddressCtrl 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CNetAddressCtrl 类"
ms.assetid: cb4c6aca-3f49-4b52-b76c-65f57096155b
caps.latest.revision: 32
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CNetAddressCtrl 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CNetAddressCtrl` 选件类表示网络地址控件，可以使用输入和验证IPv4、IPv6和名为DNS地址格式。  
  
## 语法  
  
```  
class CNetAddressCtrl : public CEdit  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CNetAddressCtrl::CNetAddressCtrl](../Topic/CNetAddressCtrl::CNetAddressCtrl.md)|构造 `CNetAddressCtrl` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CNetAddressCtrl::Create](../Topic/CNetAddressCtrl::Create.md)|使用指定的样式创建网络地址控件并将其附加到当前 `CNetAddressCtrl` 对象。|  
|[CNetAddressCtrl::CreateEx](../Topic/CNetAddressCtrl::CreateEx.md)|使用指定的扩展样式创建网络地址控件并将其附加到当前 `CNetAddressCtrl` 对象。|  
|[CNetAddressCtrl::DisplayErrorTip](../Topic/CNetAddressCtrl::DisplayErrorTip.md)|当用户在当今网络地址控件时，输入一个不受支持的网络地址显示错误气球状提示。|  
|[CNetAddressCtrl::GetAddress](../Topic/CNetAddressCtrl::GetAddress.md)|检索网络地址的验证的和分析的表示与当今网络地址控件。|  
|[CNetAddressCtrl::GetAllowType](../Topic/CNetAddressCtrl::GetAllowType.md)|检索当今网络地址控件可以支持网络地址的类型。|  
|[CNetAddressCtrl::SetAllowType](../Topic/CNetAddressCtrl::SetAllowType.md)|设置当今网络地址控件可以支持网络地址的类型。|  
  
## 备注  
 网络地址控件验证用户输入地址的格式是否正确。  控件并不实际连接到网络地址。  [CNetAddressCtrl::SetAllowType](../Topic/CNetAddressCtrl::SetAllowType.md) 方法指定 [CNetAddressCtrl::GetAddress](../Topic/CNetAddressCtrl::GetAddress.md) 方法可以分析和验证地址的一种或多种类型。  以IPv4、IPv6或命名地址服务器，网络，宿主的形式，地址可能很，或者广播消息目标。  如果地址的格式不正确，则可以使用 [CNetAddressCtrl::DisplayErrorTip](../Topic/CNetAddressCtrl::DisplayErrorTip.md) 方法显示图形方式指向网络地址控件文本框并显示预定义的错误消息中的信息提示消息框。  
  
 `CNetAddressCtrl` 选件类从 [CEdit](../../mfc/reference/cedit-class.md) 选件类派生。  因此，网络地址控件提供对所有Windows编辑控件消息。  
  
 下图显示包含一个网络地址控件的对话框。  网络地址控件的文本框\(1\)包含无效网络地址。  如果网络地址无效，信息提示消息\(2\)显示。  
  
 ![具有网络地址控件和信息提示的对话框。](../../mfc/reference/media/cnetaddctrl.png "CNetAddCtrl")  
  
## 示例  
 下面的代码示例是验证网络地址对话框的部分。  三个单选按钮的事件处理程序指定网络地址可能是三个地址类型之一。  用户在网络控件的文本框中输入地址，然后按按钮验证该地址。  如果该地址是否有效，成功将显示;否则，预定义的信息提示将显示一条错误消息。  
  
 [!code-cpp[NVC_MFC_CNetAddressCtrl_s1#1](../../mfc/reference/codesnippet/CPP/cnetaddressctrl-class_1.cpp)]  
  
## 示例  
 下面的代码示例从对话框标头文件定义 [CNetAddressCtrl::GetAddress](../Topic/CNetAddressCtrl::GetAddress.md) 方法所需的 [NC\_ADDRESS](http://msdn.microsoft.com/library/windows/desktop/bb773345) 和 [NET\_ADDRESS\_INFO](http://msdn.microsoft.com/library/windows/desktop/bb773346) 变量。  
  
 [!code-cpp[NVC_MFC_CNetAddressCtrl_s1#2](../../mfc/reference/codesnippet/CPP/cnetaddressctrl-class_2.h)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 `CNetAddressCtrl`  
  
## 要求  
 **标头:** afxcmn.h  
  
 此选件类在 [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] 和更高版本支持。  
  
 此选件类的其他要求。[Windows Vista 公共控件的生成要求](../../mfc/build-requirements-for-windows-vista-common-controls.md)所述。  
  
## 请参阅  
 [CNetAddressCtrl Class](../../mfc/reference/cnetaddressctrl-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CEdit Class](../../mfc/reference/cedit-class.md)