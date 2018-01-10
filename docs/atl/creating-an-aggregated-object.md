---
title: "创建聚合的对象 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- aggregation [C++], creating aggregated objects
- aggregate objects [C++], creating
ms.assetid: fc29d7aa-fd53-4276-9c2f-37379f71b179
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7b6b66a80c5459157b644ec6b264b707232c83e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="creating-an-aggregated-object"></a>创建聚合的对象
聚合委托**IUnknown**调用，提供指向外部对象的指针**IUnknown**内部对象。  
  
### <a name="to-create-an-aggregated-object"></a>若要创建聚合的对象  
  
1.  添加**IUnknown**指向您的类对象，并将其初始化为**NULL**构造函数中。  
  
2.  重写[FinalConstruct](../atl/reference/ccomobjectrootex-class.md#finalconstruct)创建聚合。  
  
3.  使用**IUnknown**指针，在步骤 1 中定义的第二个参数为[COM_INTERFACE_ENTRY_AGGREGATE](reference/com-interface-entry-macros.md#com_interface_entry_aggregate)宏。  
  
4.  重写[FinalRelease](../atl/reference/ccomobjectrootex-class.md#finalrelease)释放**IUnknown**指针。  
  
> [!NOTE]
>  如果使用的虚拟机和模板，发布期间的聚合对象中的接口。 `FinalConstruct`，应添加[DECLARE_PROTECT_FINAL_CONSTRUCT](reference/aggregation-and-class-factory-macros.md#declare_protect_final_construct)到你的类对象的定义的宏。  
  
## <a name="see-also"></a>请参阅  
 [ATL COM 对象基础知识](../atl/fundamentals-of-atl-com-objects.md)

