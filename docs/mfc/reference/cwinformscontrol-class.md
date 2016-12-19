---
title: "CWinFormsControl Class | Microsoft Docs"
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
  - "CWinFormsControl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWinFormsControl class"
  - "MFC [C++], Windows 窗体支持"
  - "Windows 窗体 [C++], MFC 支持"
ms.assetid: 6406dd7b-fb89-4a18-ac3a-c010d6b6289a
caps.latest.revision: 28
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CWinFormsControl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

为承载Windows窗体控件提供了基本功能。  
  
## 语法  
  
```  
template<class TManagedControl>  
class CWinFormsControl : public CWnd  
```  
  
#### 参数  
 `TManagedControl`  
 在MFC应用程序中显示的.NET Framework Windows窗体控件。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CWinFormsControl::CWinFormsControl](../Topic/CWinFormsControl::CWinFormsControl.md)|构造MFC Windows窗体控件包装对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CWinFormsControl::CreateManagedControl](../Topic/CWinFormsControl::CreateManagedControl.md)|在MFC容器创建一个Windows窗体控件。|  
|[CWinFormsControl::GetControl](../Topic/CWinFormsControl::GetControl.md)|检索指向Windows窗体控件。|  
|[CWinFormsControl::GetControlHandle](../Topic/CWinFormsControl::GetControlHandle.md)|检索句柄Windows窗体控件。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CWinFormsControl::operator \-\>](../Topic/CWinFormsControl::operator%20-%3E.md)|替换在表达式中 [CWinFormsControl::GetControl](../Topic/CWinFormsControl::GetControl.md)。|  
|[CWinFormsControl::operator TManagedControl^](../Topic/CWinFormsControl::operator%20TManagedControl%5E.md)|转换类型，指向Windows窗体控件。|  
  
## 备注  
 `CWinFormsControl` 选件类中承载Windows窗体控件提供了基本功能。  
  
 有关使用Windows窗体的更多信息，请参见 [在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
 MFC代码不应缓存窗口的句柄\(通常存储在 `m_hWnd`）。  某些Windows窗体控件属性需要使用 `DestroyWindow` 和 `CreateWindow`，基础Win32 `Window` 销毁并重新创建。  MFC Windows窗体实现处理控件的 `Destroy` 和 `Create` 事件更新 `m_hWnd` 成员。  
  
> [!NOTE]
>  MFC Windows窗体集成只在与动态链接到MFC的项目\(在其中定义了AFXDLL。）  
  
## 要求  
 **标头:** afxwinforms.h  
  
## 请参阅  
 [CWinFormsDialog Class](../../mfc/reference/cwinformsdialog-class.md)   
 [CWinFormsView Class](../../mfc/reference/cwinformsview-class.md)