---
title: "ISupportErrorInfoImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::ISupportErrorInfoImpl<piid>"
  - "ATL::ISupportErrorInfoImpl"
  - "ISupportErrorInfoImpl"
  - "ATL.ISupportErrorInfoImpl<piid>"
  - "ATL.ISupportErrorInfoImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "error information, ATL"
  - "ISupportErrorInfo ATL implementation"
  - "ISupportErrorInfoImpl class"
ms.assetid: e33a4b11-a123-41cf-bcea-7b19743902af
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# ISupportErrorInfoImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

只有一个接口在对象时，发生此错误选件类提供 [ISupportErrorInfo Interface](http://msdn.microsoft.com/zh-cn/42d33066-36b4-4a5b-aa5d-46682e560f32) 的默认实现\)，并可以使用。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]执行的应用程序。  
  
## 语法  
  
```  
  
      template<  
const IID* piid   
>  
class ATL_NO_VTABLE ISupportErrorInfoImpl :  
public ISupportErrorInfo  
```  
  
#### 参数  
 `piid`  
 对于支持 [IErrorInfo](http://msdn.microsoft.com/zh-cn/4dda6909-2d9a-4727-ae0c-b5f90dcfa447)接口的IID的指针。  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[ISupportErrorInfoImpl::InterfaceSupportsErrorInfo](../Topic/ISupportErrorInfoImpl::InterfaceSupportsErrorInfo.md)|指示 `riid` 确定接口是否支持 [IErrorInfo](http://msdn.microsoft.com/zh-cn/4dda6909-2d9a-4727-ae0c-b5f90dcfa447) 接口。|  
  
## 备注  
 [ISupportErrorInfo Interface](http://msdn.microsoft.com/zh-cn/42d33066-36b4-4a5b-aa5d-46682e560f32) 确保错误信息可以返回到客户端。  使用 **IErrorInfo** 的对象必须实现 **ISupportErrorInfo**。  
  
 只有一个接口在对象时，将生成错误选件类 `ISupportErrorInfoImpl` 提供 **ISupportErrorInfo** 的默认实现\)，并可以使用。  例如：  
  
 [!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/CPP/isupporterrorinfoimpl-class_1.h)]  
  
## 继承层次结构  
 `ISupportErrorInfo`  
  
 `ISupportErrorInfoImpl`  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [Class Overview](../../atl/atl-class-overview.md)