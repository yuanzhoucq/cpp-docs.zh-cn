---
title: "CSettingsStoreSP Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSettingsStoreSP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSettingsStoreSP class"
ms.assetid: bcd37f40-cfd4-4d17-a5ce-3bfabe995dcc
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# CSettingsStoreSP Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CSettingsStoreSP` 选件类是一个可用于创建 [CSettingsStore Class](../../mfc/reference/csettingsstore-class.md)的实例的帮助器选件类。  
  
## 语法  
  
```  
class CSettingsStoreSP  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CSettingsStoreSP::CSettingsStoreSP](../Topic/CSettingsStoreSP::CSettingsStoreSP.md)|构造 `CSettingsStoreSP` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CSettingsStoreSP::Create](../Topic/CSettingsStoreSP::Create.md)|创建从 `CSettingsStore`派生选件类的实例。|  
|[CSettingsStoreSP::SetRuntimeClass](../Topic/CSettingsStoreSP::SetRuntimeClass.md)|设置运行时选件类。  `Create` 方法使用运行时选件类确定创建的对象的选件类。|  
  
### 数据成员  
  
|名称|说明|  
|--------|--------|  
|`m_dwUserData`|在 `CSettingsStoreSP` 对象存储的自定义用户数据。  您提供在 `CSettingsStoreSP` 对象的构造函数的数据。|  
|`m_pRegistry`|`CSettingsStore`\- `Create` 方法创建的派生对象。|  
  
## 备注  
 可以使用 `CSettingsStoreSP` 选件类重所有MFC注册表操作定向到其他位置，如XML文件或数据库。  为此，请执行以下步骤：  
  
1.  创建选件类\(例如 `CMyStore`\)并从 `CSettingsStore`派生。  
  
2.  使用 [DECLARE\_DYNCREATE](../Topic/DECLARE_DYNCREATE.md) 和 [IMPLEMENT\_DYNCREATE](../Topic/IMPLEMENT_DYNCREATE.md) 宏在您的自定义 `CSettingsStore` 选件类启用动态创建。  
  
3.  重写虚函数并实现在自定义选件类的 `Read` 和 `Write` 功能。  实现其他功能读写数据。您的预期位置。  
  
4.  在应用程序中，调用 `CSettingsStoreSP::SetRuntimeClass` 并传入指针从您的选件类获取的 [CRuntimeClass Structure](../../mfc/reference/cruntimeclass-structure.md)。  
  
 每当框架通常访问注册表，它将动态现在实例化您的自定义选件类并使用它读取或写入数据。  
  
 `CSettingsStoreSP::SetRuntimeClass` 使用全局静态变量。  因此，只有一个自定义存储每个可用。  
  
## 要求  
 **标头:** afxsettingsstore.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CSettingsStore Class](../../mfc/reference/csettingsstore-class.md)