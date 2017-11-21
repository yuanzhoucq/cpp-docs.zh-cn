---
title: "DeferrableEventArgs 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: ece89267-7b72-40e1-8185-550c865b070a
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 27107c794dfd4987eb0519dfeaa9762f47d0417c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="deferrableeventargs-class"></a>DeferrableEventArgs 类
一种用于延迟的事件自变量类型的模板类。  
  
## <a name="syntax"></a>语法  
  
```cpp  
template <  
typename TEventArgsInterface,  
typename TEventArgsClass  
>  
class DeferrableEventArgs : public TEventArgsInterface  
  
```  
  
#### <a name="parameters"></a>参数  
 `TEventArgsInterface`  
 声明延迟事件的自变量的接口类型。  
  
 `TEventArgsClass`  
 可实现 `TEventArgsInterface` 的类。  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[DeferrableEventArgs::GetDeferral 方法](../windows/deferrableeventargs-getdeferral-method.md)|获取对[延迟](http://go.microsoft.com/fwlink/?LinkId=526520)对象该对象表示延迟的事件。|  
|[DeferrableEventArgs::InvokeAllFinished 方法](../windows/deferrableeventargs-invokeallfinished-method.md)|调用以指示处理延迟事件的全部过程都已完成。|  
  
## <a name="remarks"></a>备注  
 将此类的实例传递给延迟事件的事件句柄。 模板参数表示一个接口，该接口为特定类型的延迟事件定义事件参数的详细信息以及定义实现该接口的类。  
  
 此类显示为一个延迟事件的事件处理程序的第一个自变量。 你可以调用[GetDeferral](../windows/deferrableeventargs-getdeferral-method.md)方法以获取[延迟](http://go.microsoft.com/fwlink/?LinkId=526520)可以从中获取有关延迟事件的所有信息的对象。 处理完事件后，应对 Deferral 对象调用 Complete。 然后，你应调用[InvokeAllFinished](../windows/deferrableeventargs-invokeallfinished-method.md)在事件处理程序方法结束时，这可确保所有延迟事件的完成已正确传递。  
  
## <a name="requirements"></a>要求  
 **标头：** event.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>另请参阅  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)