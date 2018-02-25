---
title: "scheduler_ptr 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::get
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::operator bool
dev_langs:
- C++
ms.assetid: e88c84af-c306-476d-aef1-f42a0fa0a80f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 257dcae6df4deb0a52f7dee4db98adba2b2b4f29
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="schedulerptr-structure"></a>scheduler_ptr 结构
表示指向计划程序的指针。 此类可用于通过使用 shared_ptr 来允许指定共享生存期，或通过使用原始指针来允许指定无格式引用。  
  
## <a name="syntax"></a>语法  
  
```
struct scheduler_ptr;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[scheduler_ptr::scheduler_ptr](#ctor)|已重载。 创建一个从 shared_ptr 到计划程序的计划程序指针|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[scheduler_ptr::get](#get)|返回指向计划程序的原始指针|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[scheduler_ptr::operator bool](#operator_bool)|测试计划程序指针是否为非 null|  
|[scheduler_ptr::operator-&gt;](#operator_ptr)|行为类似于指针|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `scheduler_ptr`  
  
## <a name="requirements"></a>惠?  
 **标头：** pplinterface.h  
  
 **命名空间：** 并发  
  
##  <a name="get"></a>  scheduler_ptr:: get 方法  
 返回指向计划程序的原始指针  
  
```
scheduler_interface* get() const;
```  
  
### <a name="return-value"></a>返回值  
  
##  <a name="operator_bool"></a>  scheduler_ptr:: operator bool   
 测试计划程序指针是否为非 null  
  
'' 运算符 bool() const;
```  
  
##  <a name="operator_ptr"></a>  scheduler_ptr::operator-&gt;   
 Behave like a pointer  
  
```
scheduler_interface * 运算符-> （) const;
```  
  
### Return Value  
  
##  <a name="ctor"></a>  scheduler_ptr::scheduler_ptr Constructor  
 Creates a scheduler pointer from shared_ptr to scheduler  
  
```
explicit scheduler_ptr(std::shared_ptr<scheduler_interface> scheduler);

显式 scheduler_ptr (_In_opt_ scheduler_interface * pScheduler);
```  
  
### Parameters  
 `scheduler`  
 `pScheduler`  
  
## See Also  
 [concurrency Namespace](concurrency-namespace.md)
