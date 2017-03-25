---
title: "accelerator_view 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- accelerator_view
- AMPRT/accelerator_view
- AMPRT/Concurrency::accelerator_view:accelerator_view
- AMPRT/Concurrency::accelerator_view:create_marker
- AMPRT/Concurrency::accelerator_view:flush
- AMPRT/Concurrency::accelerator_view:get_accelerator
- AMPRT/Concurrency::accelerator_view:get_is_auto_selection
- AMPRT/Concurrency::accelerator_view:get_is_debug
- AMPRT/Concurrency::accelerator_view:get_queuing_mode
- AMPRT/Concurrency::accelerator_view:get_version
- AMPRT/Concurrency::accelerator_view:wait
- AMPRT/Concurrency::accelerator_view:accelerator
- AMPRT/Concurrency::accelerator_view:is_auto_selection
- AMPRT/Concurrency::accelerator_view:is_debug
- AMPRT/Concurrency::accelerator_view:queuing_mode
- AMPRT/Concurrency::accelerator_view:version
dev_langs:
- C++
helpviewer_keywords:
- accelerator_view class
ms.assetid: 9f298c21-bf62-46e0-88b8-01c5c78ef144
caps.latest.revision: 18
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
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: f5e6fd5689cf034cc260649fa005f7dfe6e9fd69
ms.lasthandoff: 03/17/2017

---
# <a name="acceleratorview-class"></a>accelerator_view 类
表示在 c + + AMP 数据并行快捷键上的虚拟设备抽象。  
  
### <a name="syntax"></a>语法  
  
```  
class accelerator_view;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[accelerator_view 构造函数](#ctor)|初始化 `accelerator_view` 类的新实例。|  
|[~ accelerator_view 析构函数](#dtor)|销毁`accelerator_view`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[create_marker](#create_marker)|返回将来能够跟踪对此提交到目前为止的所有命令的完成`accelerator_view`对象。|  
|[flush](#flush)|为排队的所有挂起命令提交`accelerator_view`对象传递给快捷键执行。|  
|[get_accelerator](#get_accelerator)|返回 `accelerator` 对象的 `accelerator_view` 对象。|  
|[get_is_auto_selection](#get_is_auto_selection)|返回一个布尔值，该值指示是否运行时将自动选择适当的加速器时`accelerator_view`对象传递给[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)。|  
|[get_is_debug](#get_is_debug)|返回一个布尔值，该值指示是否`accelerator_view`对象具有为广泛的错误报告启用了调试层。|  
|[get_queuing_mode](#get_queuing_mode)|返回的排队模式`accelerator_view`对象。|  
|[get_version](#get_version)|返回的版本`accelerator_view`。|  
|[等待](#wait)|等待所有命令提交给`accelerator_view`对象来完成。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[operator!=](#operator_neq)|比较此`accelerator_view`与另一个对象，并返回`false`如果它们是相同的; 否则，返回`true`。|  
|[operator=](#operator_eq)|将指定的内容复制`accelerator_view`到此对象。|  
|[operator==](#operator_eq_eq)|比较此`accelerator_view`与另一个对象，并返回`true`如果它们是相同的; 否则，返回`false`。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[加速器](#accelerator)|获取 `accelerator_view` 对象的 `accelerator` 对象。|  
|[is_auto_selection](#is_auto_selection)|获取一个布尔值，该值指示是否运行时将自动选择适当的加速器时`accelerator_view`对象传递给[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)。|  
|[is_debug](#is_debug)|获取一个布尔值，该值指示是否`accelerator_view`对象具有为广泛的错误报告启用了调试层。|  
|[queuing_mode](#queuing_mode)|获取的排队模式`accelerator_view`对象。|  
|[version](#version)|获取快捷键的版本。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `accelerator_view`  
  
### <a name="remarks"></a>备注  
 `accelerator_view`对象表示逻辑的、 独立的快捷键视图。 单个物理计算设备都可以具有许多逻辑的、 独立`accelerator_view`对象。 每个加速器有一个默认`accelerator_view`对象。 其他`accelerator_view`可能会创建对象。  
  
 可以在多个客户端线程之间共享物理设备。 客户端线程以协作方式可以使用相同的`accelerator_view`快捷键或每个客户端对象可与通过独立于计算设备通信`accelerator_view`隔离来自其他客户端线程的对象。  
  
 `accelerator_view`对象都可以有一个两个[queuing_mode 枚举](concurrency-namespace-enums-amp.md#queuing_mode)状态。 如果排队模式，则`immediate`，命令，如`copy`和`parallel_for_each`被发送到相应的加速器设备，只要它们返回给调用方。 如果排队模式，则`deferred`，此类命令在对应的命令队列上排队等候`accelerator_view`对象。 命令不会向该设备之前实际发送`flush()`调用。  
  
## <a name="requirements"></a>要求  
 **标头︰** amprt.h  
  
 **命名空间：** 并发  

## <a name="accelerator"></a>加速器 

获取 accelerator_view 对象加速器对象。  
  
### <a name="syntax"></a>语法  
  
```  
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;  
```  
  
## <a name="ctor"></a>accelerator_view 

Accelerator_view 类的新实例初始化通过复制现有`accelerator_view`对象。  
  
### <a name="syntax"></a>语法  
  
```  
accelerator_view( const accelerator_view & _Other );  
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 `accelerator_view`要从中复制对象。  
  
## <a name="accelerator_view__create_marker"></a>create_marker 

返回将来能够跟踪对此提交到目前为止的所有命令的完成`accelerator_view`对象。  
  
### <a name="syntax"></a>语法  
  
```  
concurrency::completion_future create_marker();  
```  
  
### <a name="return-value"></a>返回值  
 将来能够跟踪对此提交到目前为止的所有命令的完成`accelerator_view`对象。  
  
## <a name="flush"></a>刷新 

将提交所有挂起的命令已排入队列的 accelerator_view 对象给快捷键执行。  
  
### <a name="syntax"></a>语法  
  
```  
void flush();  
```  
  
### <a name="return-value"></a>返回值  
 返回 `void`。  

## <a name="accelerator_view__get_accelerator"></a>get_accelerator 

返回 accelerator_view 对象的加速器对象。
### <a name="syntax"></a>语法
```
accelerator get_accelerator() const;
```
### <a name="return-value"></a>返回值
Accelerator_view 对象的加速器对象。

## <a name="accelerator_view__get_is_auto_selection"></a>get_is_auto_selection 

返回一个布尔值，该值指示是否 accelerator_view 传递给时，运行时将自动选择适当的加速器[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)。  
  
### <a name="syntax"></a>语法  
  
```  
bool get_is_auto_selection() const;  
```  
  
### <a name="return-value"></a>返回值  
 `true`如果运行时将自动选择适当的加速器;否则为`false`。  
  
## <a name="accelerator_view__get_is_debug"></a>get_is_debug 

返回一个布尔值，该值指示 accelerator_view 对象是否为广泛的错误报告启用了调试层。  
  
### <a name="syntax"></a>语法  
  
```  
bool get_is_debug() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个布尔值，指示 `accelerator_view` 对象是否为广泛的错误报告启用了调试层。  

## <a name="accelerator_view__get_queuing_mode"></a>get_queuing_mode 

返回 accelerator_view 对象的排队模式。  
  
### <a name="syntax"></a>语法  
  
```  
queuing_mode get_queuing_mode() const;  
```  
  
### <a name="return-value"></a>返回值  
 `accelerator_view` 对象的排队模式。  
  
## <a name="accelerator_view__get_version"></a>get_version 

返回 accelerator_view 的版本。  
  
### <a name="syntax"></a>语法  
  
```  
unsigned int get_version() const;  
```  
  
### <a name="return-value"></a>返回值  
 版本`accelerator_view`。  
  
## <a name="accelerator_view__is_auto_selection"></a>is_auto_selection 

获取一个布尔值，该值指示是否 accelerator_view 传递给时，运行时将自动选择适当的加速器[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)。  
  
### <a name="syntax"></a>语法  
  
```  
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;  
```  
  
## <a name="accelerator_view__is_debug"></a>is_debug 

获取一个布尔值，该值指示 accelerator_view 对象是否为广泛的错误报告启用了调试层。  
  
### <a name="syntax"></a>语法  
  
```  
__declspec(property(get= get_is_debug)) bool is_debug;  
```  
  
## <a name="accelerator_view__operator_neq"></a>运算符 ！ = 

将此 accelerator_view 对象与另一个进行比较并返回`false`如果它们是相同的; 否则，返回`true`。  
  
### <a name="syntax"></a>语法  
  
```  
bool operator!= (    const accelerator_view & _Other ) const;  
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 与此对象相比较的 `accelerator_view` 对象。  
  
### <a name="return-value"></a>返回值  
 如果两个对象相同，则为 `false`；否则为 `true`。  
  
## <a name="accelerator_view__operator_eq"></a>运算符 = 

将指定的 accelerator_view 对象的内容复制到它。  
  
### <a name="syntax"></a>语法  
  
```  
accelerator_view & operator= (    const accelerator_view & _Other );  
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 `accelerator_view`从其中复制对象。  
  
### <a name="return-value"></a>返回值  
 对修改后的 `accelerator_view` 对象的引用。  
  
## <a name="accelerator_view__operator_eq_eq"></a>运算符 = = 

将此 accelerator_view 对象与另一个进行比较并返回`true`如果它们是相同的; 否则，返回`false`。  
  
### <a name="syntax"></a>语法  
  
```  
bool operator= = (    const accelerator_view & _Other ) const;  
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 与此对象相比较的 `accelerator_view` 对象。  
  
### <a name="return-value"></a>返回值  
 如果两个对象相同，则为 `true`；否则为 `false`。  
  
## <a name="accelerator_view__queuing_mode"></a>queuing_mode 

获取 accelerator_view 对象排队模式。  
  
### <a name="syntax"></a>语法  
  
```  
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;  
```  
  
## <a name="accelerator_view__version"></a>版本 

获取 accelerator_view 的版本。  
  
### <a name="syntax"></a>语法  
  
```  
__declspec(property(get= get_version)) unsigned int version;  
```  
  
## <a name="accelerator_view__wait"></a>等待 

等待所有命令提交给 accelerator_view 对象都完成。  
  
### <a name="syntax"></a>语法  
  
```  
void wait();  
```  
  
#### <a name="return-value"></a>返回值  
 返回 `void`。  
  
#### <a name="remarks"></a>备注  
 如果[queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode)是`immediate`，此方法会立即返回而不会阻止。  
  
##  <a name="dtor"></a>~ accelerator_view 

 销毁 accelerator_view 对象。  
  
#### <a name="syntax"></a>语法  
  
```  
~accelerator_view();  
```  
  
### <a name="return-value"></a>返回值  
  
 
## <a name="see-also"></a>另请参阅  
 [并发命名空间 (C++ AMP)](concurrency-namespace-cpp-amp.md)

