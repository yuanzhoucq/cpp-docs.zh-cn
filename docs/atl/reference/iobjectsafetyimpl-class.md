---
title: "IObjectSafetyImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IObjectSafetyImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "控件 [ATL], safe"
  - "IObjectSafety, ATL 实现"
  - "IObjectSafetyImpl class"
  - "safe for scripting and initialization (controls)"
ms.assetid: 64e32082-d910-4a8a-a5bf-ebed9145359d
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IObjectSafetyImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类提供 `IObjectSafety` 接口的默认实现允许客户端检索和设置对象的安全级别。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]执行的应用程序。  
  
## 语法  
  
```  
  
      template <class   
      T  
      , DWORD   
      dwSupportedSafety  
      >  
class IObjectSafetyImpl  
```  
  
#### 参数  
 `T`  
 您的选件类，从派生 `IObjectSafetyImpl`。  
  
 *dwSupportedSafety*  
 指定控件支持的安全选项。  可为下列值之一：  
  
-   应使**INTERFACESAFE\_FOR\_UNTRUSTED\_CALLER**[SetInterfaceSafetyOptions](../Topic/IObjectSafetyImpl::SetInterfaceSafetyOptions.md) 参数标识的接口 `riid` 安全性脚本。  
  
-   应使**INTERFACESAFE\_FOR\_UNTRUSTED\_DATA**`SetInterfaceSafetyOptions` 参数标识的接口 `riid` 安全性不信任的数据在初始化时。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[IObjectSafetyImpl::GetInterfaceSafetyOptions](../Topic/IObjectSafetyImpl::GetInterfaceSafetyOptions.md)|检索对象支持的安全选项，以及安全选项为对象当前设置。|  
|[IObjectSafetyImpl::SetInterfaceSafetyOptions](../Topic/IObjectSafetyImpl::SetInterfaceSafetyOptions.md)|进行初始化或脚本对象安全。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[IObjectSafetyImpl::m\_dwCurrentSafety](../Topic/IObjectSafetyImpl::m_dwCurrentSafety.md)|存储对象的当前安全级别。|  
  
## 备注  
 选件类 `IObjectSafetyImpl` 提供 `IObjectSafety`的默认实现。  `IObjectSafety` 接口允许客户端检索和设置对象的安全级别。  例如，浏览器可能调用 **IObjectSafety::SetInterfaceSafetyOptions** 进行初始化的控件脚本撰写安全或安全。  
  
 请注意使用 **CATID\_SafeForScripting** 和 **CATID\_SafeForInitializing** 组件类的 [IMPLEMENTED\_CATEGORY](../Topic/IMPLEMENTED_CATEGORY.md) 宏提供一种备选方法指定元素是安全的。  
  
 **相关文章** [ATL教程](../../atl/active-template-library-atl-tutorial.md)，[创建ATL项目](../../atl/reference/creating-an-atl-project.md)  
  
## 继承层次结构  
 `IObjectSafety`  
  
 `IObjectSafetyImpl`  
  
## 要求  
 **Header:** atlctl.h  
  
## 请参阅  
 [IObjectSafety Interface](https://msdn.microsoft.com/en-us/library/aa768224.aspx)   
 [Class Overview](../../atl/atl-class-overview.md)