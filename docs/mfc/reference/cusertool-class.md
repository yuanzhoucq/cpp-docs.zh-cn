---
title: "CUserTool Class | Microsoft Docs"
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
  - "CUserTool"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CUserTool class"
ms.assetid: 7c287d3e-d012-488d-b4e1-aa0f83f294bb
caps.latest.revision: 25
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CUserTool Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用户工具是运行外部应用程序的菜单项。  **自定义** 对话框\([CMFCToolBarsCustomizeDialog Class](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)\)的 **工具** 选项允许用户添加用户工具以及每个用户工具指定名称、说明、参数和初始内容。  
  
## 语法  
  
```  
class CUserTool : public CObject  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CUserTool::CopyIconToClipboard](../Topic/CUserTool::CopyIconToClipboard.md)||  
|[CUserTool::DrawToolIcon](../Topic/CUserTool::DrawToolIcon.md)|绘制在指定的矩形的用户工具图标。|  
|[CUserTool::GetCommand](../Topic/CUserTool::GetCommand.md)|返回包含命令文本与用户工具的字符串。|  
|[CUserTool::GetCommandId](../Topic/CUserTool::GetCommandId.md)|返回用户工具的菜单项的命令ID。|  
|[CUserTool::Invoke](../Topic/CUserTool::Invoke.md)|执行该命令与用户工具。|  
|[CUserTool::Serialize](../Topic/CUserTool::Serialize.md)|读取或写入此对象从或对存档。  （重写 [CObject::Serialize](../Topic/CObject::Serialize.md)。）|  
|[CUserTool::SetCommand](../Topic/CUserTool::SetCommand.md)|将该命令与用户工具。|  
|[CUserTool::SetToolIcon](../Topic/CUserTool::SetToolIcon.md)|从应用程序加载用户工具的图标与工具。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CUserTool::LoadDefaultIcon](../Topic/CUserTool::LoadDefaultIcon.md)|加载用户工具的默认图标。|  
  
### 数据成员  
  
|名称|说明|  
|--------|--------|  
|[CUserTool::m\_strArguments](../Topic/CUserTool::m_strArguments.md)|用户工具的命令行参数。|  
|[CUserTool::m\_strInitialDirectory](../Topic/CUserTool::m_strInitialDirectory.md)|用户工具的初始目录。|  
|[CUserTool::m\_strLabel](../Topic/CUserTool::m_strLabel.md)|在该工具的菜单项显示的工具名称。|  
  
## 备注  
 有关如何在应用程序中启用用户工具的更多信息，请参见 [CUserToolsManager Class](../../mfc/reference/cusertoolsmanager-class.md)。  
  
## 示例  
 下面的示例演示如何创建从 `CUserToolsManager` 对象的工具，设置 `m_strLabel` 成员变量，并将用户工具运行的应用程序。  此代码段是 [Visual Studio演示示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#35](../../mfc/codesnippet/CPP/cusertool-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CUserTool](../../mfc/reference/cusertool-class.md)  
  
## 要求  
 **标头:** afxusertool.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx Class](../../mfc/reference/cwinappex-class.md)   
 [CUserToolsManager Class](../../mfc/reference/cusertoolsmanager-class.md)