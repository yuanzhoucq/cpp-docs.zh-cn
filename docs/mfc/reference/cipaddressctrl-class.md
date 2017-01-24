---
title: "CIPAddressCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CIPAddressCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CIPAddressCtrl class"
  - "公共控件, Internet Explorer 4.0"
  - "Internet address edit box"
  - "Internet Explorer 4.0 common controls"
  - "Internet protocol address box"
  - "IP address control"
ms.assetid: 9764d2f4-cb14-4ba8-b799-7f57a55a47c6
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CIPAddressCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供Windows常见IP地址控件的功能。  
  
## 语法  
  
```  
class CIPAddressCtrl : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CIPAddressCtrl::CIPAddressCtrl](../Topic/CIPAddressCtrl::CIPAddressCtrl.md)|构造 `CIPAddressCtrl` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CIPAddressCtrl::ClearAddress](../Topic/CIPAddressCtrl::ClearAddress.md)|清除内容IP地址控件。|  
|[CIPAddressCtrl::Create](../Topic/CIPAddressCtrl::Create.md)|创建一个IP地址控件并将它附加到 `CIPAddressCtrl` 对象。|  
|[CIPAddressCtrl::CreateEx](../Topic/CIPAddressCtrl::CreateEx.md)|使用指定的Windows扩展的样式创建一个IP地址控件并将它附加到 `CIPAddressCtrl` 对象。|  
|[CIPAddressCtrl::GetAddress](../Topic/CIPAddressCtrl::GetAddress.md)|检索所有四个字段的地址在IP地址控件。|  
|[CIPAddressCtrl::IsBlank](../Topic/CIPAddressCtrl::IsBlank.md)|确定在IP地址控件的所有字段是否为空。|  
|[CIPAddressCtrl::SetAddress](../Topic/CIPAddressCtrl::SetAddress.md)|将所有四个字段的地址在IP地址控件。|  
|[CIPAddressCtrl::SetFieldFocus](../Topic/CIPAddressCtrl::SetFieldFocus.md)|设置键盘焦点设置在IP地址控件的指定的字段。|  
|[CIPAddressCtrl::SetFieldRange](../Topic/CIPAddressCtrl::SetFieldRange.md)|设置指定字段的大小在IP地址控件。|  
  
## 备注  
 IP地址控件，则控件与编辑控件，在internet协议\(IP\)格式可以输入和操作数值地址。  
  
 此控件\(并 `CIPAddressCtrl` 选件类\)对于运行Microsoft Internet Explorer 4.0下的程序可用和更高版本。  它们还将在Windows和Windows NT下的未来版本。  
  
 有关IP地址控件的信息，请参见。[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [IP地址控件](http://msdn.microsoft.com/library/windows/desktop/bb761372)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CIPAddressCtrl`  
  
## 要求  
 **Header:** afxcmn.h  
  
## 请参阅  
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)