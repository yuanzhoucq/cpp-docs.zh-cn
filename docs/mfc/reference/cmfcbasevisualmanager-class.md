---
title: "CMFCBaseVisualManager Class | Microsoft Docs"
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
  - "CMFCBaseVisualManager"
  - "CMFCBaseVisualManager.~CMFCBaseVisualManager"
  - "~CMFCBaseVisualManager"
  - "CMFCBaseVisualManager::~CMFCBaseVisualManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "~CMFCBaseVisualManager destructor"
  - "CMFCBaseVisualManager class"
  - "CMFCBaseVisualManager class, 析构函数"
ms.assetid: d56f3afc-cdea-4de1-825a-a08999c571e0
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCBaseVisualManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在派生的视觉管理器和Windows API主题之间的层。  
  
 `CMFCBaseVisualManager` 加载UxTheme.dll，如果有，并管理对Windows主题API方法。  
  
 此选件类仅供内部使用。  
  
## 语法  
  
```  
class CMFCBaseVisualManager: public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|||  
|-|-|  
|名称|说明|  
|[CMFCBaseVisualManager::CMFCBaseVisualManager](../Topic/CMFCBaseVisualManager::CMFCBaseVisualManager.md)|构造和初始化 `CMFCBaseVisualManager` 对象。|  
|`CMFCBaseVisualManager::~CMFCBaseVisualManager`|析构函数。|  
  
### 公共方法  
  
|||  
|-|-|  
|名称|说明|  
|[CMFCBaseVisualManager::DrawCheckBox](../Topic/CMFCBaseVisualManager::DrawCheckBox.md)|使用当前Windows主题，绘制checkbox控件。|  
|[CMFCBaseVisualManager::DrawComboBorder](../Topic/CMFCBaseVisualManager::DrawComboBorder.md)|使用当前Windows主题，分区组合框边框。|  
|[CMFCBaseVisualManager::DrawComboDropButton](../Topic/CMFCBaseVisualManager::DrawComboDropButton.md)|使用当前Windows主题，绘制一个组合框下拉式按钮。|  
|[CMFCBaseVisualManager::DrawPushButton](../Topic/CMFCBaseVisualManager::DrawPushButton.md)|使用当前Windows主题，绘制普通按钮。|  
|[CMFCBaseVisualManager::DrawRadioButton](../Topic/CMFCBaseVisualManager::DrawRadioButton.md)|使用当前Windows主题，绘制单选按钮控件。|  
|[CMFCBaseVisualManager::DrawStatusBarProgress](../Topic/CMFCBaseVisualManager::DrawStatusBarProgress.md)|绘制在状态栏控件\([CMFCStatusBar Class](../../mfc/reference/cmfcstatusbar-class.md)\)的一个进度栏使用当前Windows主题。|  
|[CMFCBaseVisualManager::FillReBarPane](../Topic/CMFCBaseVisualManager::FillReBarPane.md)|使用当前Windows主题，加载rebar控件的背景。|  
|[CMFCBaseVisualManager::GetStandardWindowsTheme](../Topic/CMFCBaseVisualManager::GetStandardWindowsTheme.md)|获取当前Windows主题。|  
  
### 受保护的方法  
  
|||  
|-|-|  
|名称|说明|  
|[CMFCBaseVisualManager::CleanUpThemes](../Topic/CMFCBaseVisualManager::CleanUpThemes.md)|调用 `UpdateSystemColors`获得的任何句柄的 `CloseThemeData`。|  
|[CMFCBaseVisualManager::UpdateSystemColors](../Topic/CMFCBaseVisualManager::UpdateSystemColors.md)|调用 `OpenThemeData` 获取绘制的各种控件处理:窗口，工具栏，按钮，依此类推。|  
  
## 备注  
 您不必直接实例化此类选件对象。  
  
 由于它是所有视觉管理器的基类，使用该指针，可以调用 [CMFCVisualManager::GetInstance](../Topic/CMFCVisualManager::GetInstance.md)，获取指向当前视觉管理器和访问 `CMFCBaseVisualManager` 的方法。  但是，因此，如果使用当前Windows主题，则您必须将控件，请使用 `CMFCVisualManagerWindows` 接口最好。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)  
  
## 要求  
 **标头:** afxvisualmanager.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)