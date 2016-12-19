---
title: "IAccessorImpl 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IAccessorImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IAccessorImpl 类"
ms.assetid: 768606da-8b71-417c-a62c-88069ce7730d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IAccessorImpl 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供 [IAccessor](https://msdn.microsoft.com/en-us/library/ms719672.aspx) 接口的实现。  
  
## 语法  
  
```  
template <  
   class T,   
   class BindType = ATLBINDINGS,   
   class BindingVector = CAtlMap <   
      HACCESSOR hAccessor,   
      BindType* pBindingsStructure   
   >   
>  
class ATL_NO_VTABLE IAccessorImpl : public IAccessorImplBase<BindType>  
```  
  
#### 参数  
 `T`  
 行集合或命令对象类。  
  
 `BindType`  
 存储单元的绑定信息。  默认值为 **ATLBINDINGS** 结构 \(请参见 atldb.h\)。  
  
 `BindingVector`  
 存储单元的列信息。  默认是关键元素是值 **HACCESSOR** 的 [CAtlMap](../../atl/reference/catlmap-class.md)，并且值元素是指向 `BindType` 结构。  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)|构造函数。|  
  
### 接口方法  
  
|||  
|-|-|  
|[AddRefAccessor](../../data/oledb/iaccessorimpl-addrefaccessor.md)|向现有的访问器添加引用数。|  
|[CreateAccessor](../../data/oledb/iaccessorimpl-createaccessor.md)|从一组绑定创建访问器。|  
|[GetBindings](../../data/oledb/iaccessorimpl-getbindings.md)|返回访问器中的绑定。|  
|[ReleaseAccessor](../../data/oledb/iaccessorimpl-releaseaccessor.md)|释放访问器。|  
  
## 备注  
 这对行集合和命令是强制性的。  OLE DB 要求提供程序实现 **HACCESSOR**，是标记为一个 [DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) 结构。  `IAccessorImpl`提供的**HACCESSOR** 是 `BindType` 结构的地址。  默认情况下，`BindType` 被定义为 `IAccessorImpl` 模板定义的 **ATLBINDINGS**。  `BindType` `IAccessorImpl` 用于提供的机制使跟踪元素的数目。其 **DBBINDING** 数组以及引用计数和访问器标记。  
  
## 要求  
 **头文件:** atldb.h  
  
## 请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)