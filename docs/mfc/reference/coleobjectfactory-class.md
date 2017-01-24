---
title: "COleObjectFactory Class | Microsoft Docs"
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
  - "COleObjectFactory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "class factories, COleObjectFactory class"
  - "COleObjectFactory class"
  - "对象创建, OLE 对象"
  - "对象 [C++], 创建 OLE"
  - "OLE class factory"
  - "OLE 对象"
  - "OLE 对象, 创建"
  - "OLE, class factory"
ms.assetid: ab179c1e-4af2-44aa-a576-37c48149b427
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleObjectFactory Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现OLE选件类工厂，创建OLE对象\(例如服务器，自动化对象，并记录。  
  
## 语法  
  
```  
class COleObjectFactory : public CCmdTarget  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleObjectFactory::COleObjectFactory](../Topic/COleObjectFactory::COleObjectFactory.md)|构造 `COleObjectFactory` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleObjectFactory::GetClassID](../Topic/COleObjectFactory::GetClassID.md)|返回此工厂创建对象的OLE选件类ID。|  
|[COleObjectFactory::IsLicenseValid](../Topic/COleObjectFactory::IsLicenseValid.md)|确定控件的许可证是否有效。|  
|[COleObjectFactory::IsRegistered](../Topic/COleObjectFactory::IsRegistered.md)|一个工厂是否向OLE系统DLL注册。|  
|[COleObjectFactory::Register](../Topic/COleObjectFactory::Register.md)|注册了OLE系统的DLL此对象工厂。|  
|[COleObjectFactory::RegisterAll](../Topic/COleObjectFactory::RegisterAll.md)|应用程序的对象工厂注册都具有OLE系统的DLL。|  
|[COleObjectFactory::Revoke](../Topic/COleObjectFactory::Revoke.md)|取消与OLE系统DLL将此对象工厂注册。|  
|[COleObjectFactory::RevokeAll](../Topic/COleObjectFactory::RevokeAll.md)|取消应用程序的对象与OLE系统DLL的工厂注册。|  
|[COleObjectFactory::UnregisterAll](../Topic/COleObjectFactory::UnregisterAll.md)|应用程序的对象工厂的取消整个。|  
|[COleObjectFactory::UpdateRegistry](../Topic/COleObjectFactory::UpdateRegistry.md)|注册了OLE系统注册表的此对象工厂。|  
|[COleObjectFactory::UpdateRegistryAll](../Topic/COleObjectFactory::UpdateRegistryAll.md)|应用程序的对象工厂注册都具有OLE系统注册表中。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[COleObjectFactory::GetLicenseKey](../Topic/COleObjectFactory::GetLicenseKey.md)|请求从控件的DLL的唯一键。|  
|[COleObjectFactory::OnCreateObject](../Topic/COleObjectFactory::OnCreateObject.md)|调用由框架创建此工厂的类型的新对象。|  
|[COleObjectFactory::VerifyLicenseKey](../Topic/COleObjectFactory::VerifyLicenseKey.md)|验证在控件中嵌入的密钥与容器中的密钥。|  
|[COleObjectFactory::VerifyUserLicense](../Topic/COleObjectFactory::VerifyUserLicense.md)|验证控件以允许进行设计时使用。|  
  
## 备注  
 `COleObjectFactory` 选件类具有执行的以下功能成员函数:  
  
-   管理对象的注册。  
  
-   更新OLE系统注册，以及通知OLE的运行时注册对象运行和准备接收消息。  
  
-   强制允许通过限制对控件的用于授权的开发人员在设计时以及允许应用程序在运行时。  
  
-   注册控件具有OLE系统注册表的对象工厂。  
  
 有关创建对象的更多信息，请参见位于 [数据对象和数据源\(OLE\)](../../mfc/data-objects-and-data-sources-ole.md) 和 [数据对象和数据源:创建和析构](../../mfc/data-objects-and-data-sources-creation-and-destruction.md)。  有关更多信息注册，请参见文章 [注册](../../mfc/registration.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleObjectFactory`  
  
## 要求  
 **Header:** afxdisp.h  
  
## 请参阅  
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleTemplateServer Class](../../mfc/reference/coletemplateserver-class.md)