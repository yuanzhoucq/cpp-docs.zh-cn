---
title: "CComObjectRootEx Class | Microsoft Docs"
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
  - "ATL.CComObjectRootEx"
  - "ATL::CComObjectRootEx<ThreadModel>"
  - "CComObjectRootEx"
  - "ATL::CComObjectRootEx"
  - "ATL.CComObjectRootEx<ThreadModel>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "reference counting"
ms.assetid: 894a3d7c-2daf-4fd0-8fa4-e6a05bcfb631
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComObjectRootEx Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类提供了处理对象引用nonaggregated和聚合的对象的计数管理。  
  
## 语法  
  
```  
  
      template<  
   class ThreadModel   
>  
class CComObjectRootEx : public CComObjectRootBase  
```  
  
#### 参数  
 `ThreadModel`  
 方法实现所需的线程模型的选件类。  可以通过设置 `ThreadModel` 显式选择线程模型。[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)、 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)或 [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)。  可以通过设置 `ThreadModel` 接受服务器上的默认线程模型。[CComObjectThreadModel](../Topic/CComObjectThreadModel.md) 或 [CComGlobalsThreadModel](../Topic/CComGlobalsThreadModel.md)。  
  
## 成员  
  
### 方法  
  
|||  
|-|-|  
|[CComObjectRootEx](../Topic/CComObjectRootEx::CComObjectRootEx.md)|构造函数。|  
|[InternalAddRef](../Topic/CComObjectRootEx::InternalAddRef.md)|添加一个nonaggregated对象的引用计数。|  
|[InternalRelease](../Topic/CComObjectRootEx::InternalRelease.md)|减nonaggregated对象的引用计数。|  
|[锁定](../Topic/CComObjectRootEx::Lock.md)|如果线程模型多线程，获取一个临界区对象的所有权。|  
|[unlock](../Topic/CComObjectRootEx::Unlock.md)|如果线程模型多线程，您可以与临界区对象的所有权。|  
  
### CComObjectRootBase方法  
  
|||  
|-|-|  
|[FinalConstruct](../Topic/CComObjectRootEx::FinalConstruct.md)|在执行任何初始化的选件类的重写需要由您的对象。|  
|[FinalRelease](../Topic/CComObjectRootEx::FinalRelease.md)|在执行任何清理的选件类的重写需要由您的对象。|  
|[OuterAddRef](../Topic/CComObjectRootEx::OuterAddRef.md)|添加一个聚合的对象的引用计数。|  
|[OuterQueryInterface](../Topic/CComObjectRootEx::OuterQueryInterface.md)|一个复合对象的外部 **IUnknown** 的委托。|  
|[OuterRelease](../Topic/CComObjectRootEx::OuterRelease.md)|天数进行聚合的对象的引用计数。|  
  
### 静态函数  
  
|||  
|-|-|  
|[InternalQueryInterface](../Topic/CComObjectRootEx::InternalQueryInterface.md)|一nonaggregated对象的 **IUnknown** 的委托。|  
|[ObjectMain](../Topic/CComObjectRootEx::ObjectMain.md)|对模块初始化和终止时的派生类在对象图中列出。|  
  
### 数据成员  
  
|||  
|-|-|  
|[m\_dwRef](../Topic/CComObjectRootEx::m_dwRef.md)|`m_pOuterUnknown`的一部分，联合。  使用对象时，不聚合持有引用计数 `AddRef` 和 **Release**。|  
|[m\_pOuterUnknown](../Topic/CComObjectRootEx::m_pOuterUnknown.md)|`m_dwRef`的一部分，联合。  使用对象时，聚合存储指针到外部未知。|  
  
## 备注  
 `CComObjectRootEx` 处理对象引用nonaggregated和聚合的对象的计数管理。  它保留对象引用计数，如果您的对象不进行聚合，并存储指针给外部未知，如果您的对象进行聚合。  对聚合的对象，`CComObjectRootEx` 方法可用于处理内部对象的失败到构造的，因此，防止删除的外部对象，释放内部接口或内部对象被删除。  
  
 实现COM服务器的选件类必须从 `CComObjectRootEx` 或 [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)继承。  
  
 如果您的类定义指定 [DECLARE\_POLY\_AGGREGATABLE](../Topic/DECLARE_POLY_AGGREGATABLE.md) 宏，ATL创建 **CComPolyObject\<CYourClass\>** 的实例，将 **IClassFactory::CreateInstance** 调用时。  在创建时，外部未知的值进行检查。  如果是 **NULL**，**IUnknown** 为一nonaggregated对象实现。  如果外部未知不是 **NULL**，**IUnknown** 为一个复合的对象实现。  
  
 如果您的选件类不指定 `DECLARE_POLY_AGGREGATABLE` 宏，ATL创建 **CAggComObject\<CYourClass\>** 实例聚合的对象的或 **CComObject\<CYourClass\>** 实例nonaggregated对象的。  
  
 使用 `CComPolyObject` 的优点是您避免为 `CComAggObject` 和 `CComObject` 在的模块处理合成和nonaggregated大小写。  一个 `CComPolyObject` 对象处理两种情况。  因此，只有一个副本的vtable和函数的一个副本存在于您的模块。  如果vtable大，则可以显着降低您的模块范围。  但是，因此，如果vtable很小，使用 `CComPolyObject` 从而导致一个稍微大的模块范围，因为它没有为一个复合的或nonaggregated对象转换，如 `CComAggObject` 和 `CComObject`。  
  
 如果您的对象进行聚合，[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 由 `CComAggObject` 或 `CComPolyObject`实现。  这些选件类委托 `QueryInterface`，`AddRef`，并且，**Release** 调用`CComObjectRootEx`的 `OuterQueryInterface`、 `OuterAddRef`和 `OuterRelease` 转发到外部未知。  通常，可以复盖您的选件类的 `CComObjectRootEx::FinalConstruct` 创建所有聚合的对象，并重写 `CComObjectRootEx::FinalRelease` 释放任何聚合的对象。  
  
 如果您的对象不进行聚合，**IUnknown** 由 `CComObject` 或 `CComPolyObject`实现。  在这种情况下，调用 `QueryInterface`，`AddRef`，并且，**Release** 将委托给`CComObjectRootEx`的 `InternalQueryInterface`、 `InternalAddRef`和 `InternalRelease` 执行实际操作。  
  
## 要求  
 **Header:** atlcom.h  
  
## 请参阅  
 [CComAggObject Class](../../atl/reference/ccomaggobject-class.md)   
 [CComObject Class](../../atl/reference/ccomobject-class.md)   
 [CComPolyObject Class](../../atl/reference/ccompolyobject-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)