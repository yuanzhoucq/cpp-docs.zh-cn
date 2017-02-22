---
title: "IRunnableObjectImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IRunnableObjectImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "容器, running controls"
  - "控件 [ATL], 运行"
  - "控件 [C++], container running in ATL"
  - "IRunnableObject, ATL 实现"
  - "IRunnableObjectImpl class"
ms.assetid: 305c7c3b-889e-49dd-aca1-34379c1b9931
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# IRunnableObjectImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类实现 **IUnknown** 并提供 [IRunnableObject](http://msdn.microsoft.com/library/windows/desktop/ms692783) 接口的默认实现。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]执行的应用程序。  
  
## 语法  
  
```  
  
      template< class   
      T  
      >  
class IRunnableObjectImpl  
```  
  
#### 参数  
 `T`  
 您的选件类，从派生 `IRunnableObjectImpl`。  
  
## 成员  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[IRunnableObjectImpl::GetRunningClass](../Topic/IRunnableObjectImpl::GetRunningClass.md)|返回一个运行的控件的CLSID。  ATL实现一组CLSID对 `GUID_NULL` 并返回 **E\_UNEXPECTED**。|  
|[IRunnableObjectImpl::IsRunning](../Topic/IRunnableObjectImpl::IsRunning.md)|确定控件是否正在运行。  ATL实现返回 **TRUE**。|  
|[IRunnableObjectImpl::LockRunning](../Topic/IRunnableObjectImpl::LockRunning.md)|将控件锁定到运行的状态中。  ATL实现返回 `S_OK`。|  
|[IRunnableObjectImpl::Run](../Topic/IRunnableObjectImpl::Run.md)|强制该控件运行。  ATL实现返回 `S_OK`。|  
|[IRunnableObjectImpl::SetContainedObject](../Topic/IRunnableObjectImpl::SetContainedObject.md)|指示嵌入该控件。  ATL实现返回 `S_OK`。|  
  
## 备注  
 [IRunnableObject](http://msdn.microsoft.com/library/windows/desktop/ms692783) 接口允许容器确定控件是否运行，强制遇到或锁定如果该运行的状态。  选件类 `IRunnableObjectImpl` 提供此接口的默认实现并将信息发送实现 **IUnknown** 到转储计算机进行编译。  
  
 **相关文章** [ATL教程](../../atl/active-template-library-atl-tutorial.md)，[创建ATL项目](../../atl/reference/creating-an-atl-project.md)  
  
## 继承层次结构  
 `IRunnableObject`  
  
 `IRunnableObjectImpl`  
  
## 要求  
 **Header:** atlctl.h  
  
## 请参阅  
 [CComControl Class](../../atl/reference/ccomcontrol-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)