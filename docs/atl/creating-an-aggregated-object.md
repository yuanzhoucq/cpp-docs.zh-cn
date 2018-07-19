---
title: 创建聚合的对象 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- aggregation [C++], creating aggregated objects
- aggregate objects [C++], creating
ms.assetid: fc29d7aa-fd53-4276-9c2f-37379f71b179
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8f6ff5a0fdcff62d62469f17388f633b83739a09
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850821"
---
# <a name="creating-an-aggregated-object"></a>创建聚合的对象
聚合委托`IUnknown`调用，提供指向外部对象的指针`IUnknown`内部对象。  
  
### <a name="to-create-an-aggregated-object"></a>若要创建聚合的对象  
  
1.  添加`IUnknown`指向您的类对象，并在构造函数中将其初始化为 NULL。  
  
2.  重写[FinalConstruct](../atl/reference/ccomobjectrootex-class.md#finalconstruct)创建聚合函数。  
  
3.  使用`IUnknown`指针，在步骤 1 中定义的第二个参数为[COM_INTERFACE_ENTRY_AGGREGATE](reference/com-interface-entry-macros.md#com_interface_entry_aggregate)宏。  
  
4.  重写[FinalRelease](../atl/reference/ccomobjectrootex-class.md#finalrelease)释放`IUnknown`指针。  
  
> [!NOTE]
>  如果你使用和发布期间聚合的对象中的接口。 `FinalConstruct`，则应将添加[DECLARE_PROTECT_FINAL_CONSTRUCT](reference/aggregation-and-class-factory-macros.md#declare_protect_final_construct)到类对象定义的宏。  
  
## <a name="see-also"></a>请参阅  
 [ATL COM 对象基础知识](../atl/fundamentals-of-atl-com-objects.md)

