---
title: "task_handle 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ppl/concurrency::task_handle
dev_langs:
- C++
helpviewer_keywords:
- task_handle class
ms.assetid: 74a34b15-708b-4231-a509-947874292b13
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: b113cf519f4326650dc1ed4d20dd2ed00921eda9
ms.lasthandoff: 02/24/2017

---
# <a name="taskhandle-class"></a>task_handle 类
`task_handle` 类表示单个并行工作项。 它封装执行一项工作所需的指令和数据。  
  
## <a name="syntax"></a>语法  
  
```  
template<
    typename _Function  
>  
class task_handle : public ::Concurrency::details::_UnrealizedChore;  
```  
  
#### <a name="parameters"></a>参数  
 `_Function`  
 将调用以执行表示的工作的函数对象类型`task_handle`对象。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[task_handle 构造函数](#ctor)|构造一个新`task_handle`对象。 通过调用作为构造函数的参数指定的函数执行任务的工作。|  
|[~ task_handle 析构函数](#dtor)|销毁`task_handle`对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[operator （) 运算符](#task_handle__operator_call)|运行时将调用来执行的任务句柄的工作函数调用运算符。|  
  
## <a name="remarks"></a>备注  
 `task_handle`对象可以配合使用`structured_task_group`或更多常规`task_group`对象，以将工作分解为并行任务。 有关详细信息，请参阅[任务并行](../../../parallel/concrt/task-parallelism-concurrency-runtime.md)。  
  
 请注意，创建者的`task_handle`对象负责维护创建的生存期`task_handle`对象，直到它不再必需的并发运行时。 通常情况下，这意味着`task_handle`对象必须销毁，直到`wait`或`run_and_wait`方法`task_group`或`structured_task_group`已向其排队调用。  
  
 `task_handle`对象通常是与 c + + lambda 结合使用。 因为您不知道的 lambda 的真实类型[make_task](concurrency-namespace-functions.md#make_task)函数通常用于创建`task_handle`对象。  
  
 运行时创建的副本传递给函数的工作函数`task_handle`对象。 因此，在函数中发生的任何状态变更对象传递给`task_handle`对象将不会显示在该函数对象的副本中。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `task_handle`  
  
## <a name="requirements"></a>要求  
 **标头︰** ppl.h  
  
 **命名空间：** 并发  
  
##  <a name="a-nametaskhandleoperatorcalla-operator"></a><a name="task_handle__operator_call"></a>operator （) 

 运行时将调用来执行的任务句柄的工作函数调用运算符。  
  
```  
void operator()() const;

 
```  
  
##  <a name="a-nametaskhandlectora-taskhandle"></a><a name="task_handle__ctor"></a>task_handle 

 构造一个新`task_handle`对象。 通过调用作为构造函数的参数指定的函数执行任务的工作。  
  
```  
task_handle(const _Function& _Func);
```  
  
### <a name="parameters"></a>参数  
 `_Func`  
 该函数将调用以执行所代表的工时`task_handle`对象。 这可能是 lambda 伪函数、 指向函数的指针或任意对象支持的版本与签名的函数调用运算符`void operator()()`。  
  
### <a name="remarks"></a>备注  
 运行时创建的副本传递到构造函数的工作函数。 因此，在函数中发生的任何状态变更对象传递给`task_handle`对象将不会显示在该函数对象的副本中。  
  
##  <a name="a-namedtora-taskhandle"></a><a name="dtor"></a>~ task_handle 

 销毁`task_handle`对象。  
  
```  
~task_handle();
```  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [task_group 类](task-group-class.md)   
 [structured_task_group 类](structured-task-group-class.md)

