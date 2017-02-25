---
title: "CKeyboardManager Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CKeyboardManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CKeyboardManager class"
ms.assetid: 4809ece6-89df-4479-8b53-9bf476ee107b
caps.latest.revision: 33
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 35
---
# CKeyboardManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

管理主框架窗口和从子框架窗口的热键表。  
  
## 语法  
  
```  
class CKeyboardManager : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|||  
|-|-|  
|名称|说明|  
|[CKeyboardManager::CKeyboardManager](../Topic/CKeyboardManager::CKeyboardManager.md)|构造 `CKeyboardManager` 对象。|  
  
### 公共方法  
  
|||  
|-|-|  
|名称|说明|  
|[CKeyboardManager::CleanUp](../Topic/CKeyboardManager::CleanUp.md)|收拾热键桌子。|  
|[CKeyboardManager::FindDefaultAccelerator](../Topic/CKeyboardManager::FindDefaultAccelerator.md)|检索指定的命令和窗口的默认热键。|  
|[CKeyboardManager::IsKeyHandled](../Topic/CKeyboardManager::IsKeyHandled.md)|确定键是否由快捷键对应表的过程。|  
|[CKeyboardManager::IsKeyPrintable](../Topic/CKeyboardManager::IsKeyPrintable.md)|指示字符是否可打印的。|  
|[CKeyboardManager::IsShowAllAccelerators](../Topic/CKeyboardManager::IsShowAllAccelerators.md)|指示是否显示菜单命令或仅默认热键的所有热键。|  
|[CKeyboardManager::LoadState](../Topic/CKeyboardManager::LoadState.md)|从Windows注册表加载热键表。|  
|[CKeyboardManager::ResetAll](../Topic/CKeyboardManager::ResetAll.md)|重载从应用程序资源的热键表。|  
|[CKeyboardManager::SaveState](../Topic/CKeyboardManager::SaveState.md)|保存热键表与Windows注册表。|  
|[CKeyboardManager::ShowAllAccelerators](../Topic/CKeyboardManager::ShowAllAccelerators.md)|为每个命令指定框架是显示所有命令的所有热键，而一个热键。  此方法不影响只有一个关联的热键的命令。|  
|[CKeyboardManager::TranslateCharToUpper](../Topic/CKeyboardManager::TranslateCharToUpper.md)|将字符转换为其\+上面注册。|  
|[CKeyboardManager::UpdateAccelTable](../Topic/CKeyboardManager::UpdateAccelTable.md)|更新的一个新的热键表的一个热键表。|  
  
## 备注  
 此选件类的成员可以保存和加载热键到Windows注册表，使用模板更新快速的主键表和查找某个命令的默认热键在框架窗口。  此外，`CKeyboardManager` 对象可以控制热键如何显示给用户。  
  
 您不应该手动创建 `CKeyboardManager` 对象。  它将由应用程序框架自动创建。  但是，您应调用时 [CWinAppEx::InitKeyboardManager](../Topic/CWinAppEx::InitKeyboardManager.md) 初始化过程您的应用程序。  获取对键盘管理器的指针应用程序中，调用 [CWinAppEx::GetKeyboardManager](../Topic/CWinAppEx::GetKeyboardManager.md)。  
  
## 示例  
 下面的示例演示如何检索指向 `CKeyboardManager` 对象从 `CWinAppEx` 选件类以及如何显示所有热键与菜单命令。  此代码段是 [自定义调用示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_CustomPages#5](../../mfc/reference/codesnippet/CPP/ckeyboardmanager-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)  
  
## 要求  
 **标头:** afxkeyboardmanager.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx Class](../../mfc/reference/cwinappex-class.md)   
 [CWinAppEx::InitKeyboardManager](../Topic/CWinAppEx::InitKeyboardManager.md)   
 [键盘和鼠标自定义](../../mfc/keyboard-and-mouse-customization.md)