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
- amprt/Concurrency::accelerator_view
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
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: 78569f1ff21af3ed05cb908a851f0fe05d5d271a
ms.lasthandoff: 02/24/2017

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
  
|名称|说明|  
|----------|-----------------|  
|[create_marker 方法](#create_marker)|返回将来能够跟踪对此提交到目前为止的所有命令的完成`accelerator_view`对象。|  
|[flush 方法](#flush)|为排队的所有挂起命令提交`accelerator_view`对象传递给快捷键执行。|  
|[get_accelerator 方法](#get_accelerator)|返回 `accelerator` 对象的 `accelerator_view` 对象。|  
|[get_is_auto_selection 方法](#get_is_auto_selection)|返回一个布尔值，该值指示是否运行时将自动选择适当的加速器时`accelerator_view`对象传递给[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)。|  
|[get_is_debug 方法](#get_is_debug)|返回一个布尔值，该值指示是否`accelerator_view`对象具有为广泛的错误报告启用了调试层。|  
|[get_queuing_mode 方法](#get_queuing_mode)|返回的排队模式`accelerator_view`对象。|  
|[get_version 方法](#get_version)|返回的版本`accelerator_view`。|  
|[wait 方法](#wait)|等待所有命令提交给`accelerator_view`对象来完成。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[运算符 ！ = 运算符](#operator_neq)|比较此`accelerator_view`与另一个对象，并返回`false`如果它们是相同的; 否则，返回`true`。|  
|[运算符 = 运算符](#operator_eq)|将指定的内容复制`accelerator_view`到此对象。|  
|[运算符 = = 运算符](#operator_eq_eq)|比较此`accelerator_view`与另一个对象，并返回`true`如果它们是相同的; 否则，返回`false`。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[accelerator 数据成员](#accelerator)|获取 `accelerator_view` 对象的 `accelerator` 对象。|  
|[is_auto_selection 数据成员](#is_auto_selection)|获取一个布尔值，该值指示是否运行时将自动选择适当的加速器时`accelerator_view`对象传递给[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)。|  
|[is_debug 数据成员](#is_debug)|获取一个布尔值，该值指示是否`accelerator_view`对象具有为广泛的错误报告启用了调试层。|  
|[queuing_mode 数据成员](#queuing_mode)|获取的排队模式`accelerator_view`对象。|  
|[版本的数据成员](#version)|获取快捷键的版本。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `accelerator_view`  
  
### <a name="remarks"></a>备注  
 `accelerator_view`对象表示逻辑的、 独立的快捷键视图。 单个物理计算设备都可以具有许多逻辑的、 独立`accelerator_view`对象。 每个加速器有一个默认`accelerator_view`对象。 其他`accelerator_view`可能会创建对象。  
  
 可以在多个客户端线程之间共享物理设备。 客户端线程以协作方式可以使用相同的`accelerator_view`快捷键或每个客户端对象可与通过独立于计算设备通信`accelerator_view`隔离来自其他客户端线程的对象。  
  
 `accelerator_view`对象都可以有一个两个[queuing_mode 枚举](concurrency-namespace-enums-amp.md#queuing_mode)状态。 如果排队模式，则`immediate`，命令，如`copy`和`parallel_for_each`被发送到相应的加速器设备，只要它们返回给调用方。 如果排队模式，则`deferred`，此类命令在对应的命令队列上排队等候`accelerator_view`对象。 命令不会向该设备之前实际发送`flush()`调用。  
  
## <a name="requirements"></a>要求  
 **标头︰** amprt.h  
  
 **命名空间：** 并发  

## <a name="a-nameacceleratora-accelerator"></a><a name="accelerator"></a>加速器 

获取 accelerator_view 对象加速器对象。  
  
### <a name="syntax"></a>语法  
  
```  
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;  
```  
  
## <a name="a-namectora-acceleratorview"></a><a name="ctor"></a>accelerator_view 

Accelerator_view 类的新实例初始化通过复制现有`accelerator_view`对象。  
  
### <a name="syntax"></a>语法  
  
```  
accelerator_view( const accelerator_view & _Other );  
```  
  
### <a name="parameters"></a>参数  
 `_Other`  
 `accelerator_view`要从中复制对象。  
  
## <a name="a-nameacceleratorviewcreatemarkera-createmarker"></a><a name="accelerator_view__create_marker"></a>create_marker 

返回将来能够跟踪对此提交到目前为止的所有命令的完成`accelerator_view`对象。  
  
### <a name="syntax"></a>语法  
  
```  
concurrency::completion_future create_marker();  
```  
  
### <a name="return-value"></a>返回值  
 将来能够跟踪对此提交到目前为止的所有命令的完成`accelerator_view`对象。  
  
## <a name="a-nameflusha-flush"></a><a name="flush"></a>刷新 

将提交所有挂起的命令已排入队列的 accelerator_view 对象给快捷键执行。  
  
### <a name="syntax"></a>语法  
  
```  
void flush();  
```  
  
### <a name="return-value"></a>返回值  
 返回 `void`。  

## <a name="a-nameacceleratorviewgetacceleratora-getaccelerator"></a><a name="accelerator_view__get_accelerator"></a>get_accelerator 

返回 accelerator_view 对象的加速器对象。
### <a name="syntax"></a>语法
```
accelerator get_accelerator() const;
```
### <a name="return-value"></a>返回值
Accelerator_view 对象的加速器对象。

## <a name="a-nameacceleratorviewgetisautoselectiona-getisautoselection"></a><a name="accelerator_view__get_is_auto_selection"></a>get_is_auto_selection 

返回一个布尔值，该值指示是否 accelerator_view 传递给时，运行时将自动选择适当的加速器[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)。  
  
### <a name="syntax"></a>语法  
  
```  
bool get_is_auto_selection() const;  
```  
  
### <a name="return-value"></a>返回值  
 `true`如果运行时将自动选择适当的加速器;否则为`false`。  
  
## <a name="a-nameacceleratorviewgetisdebuga-getisdebug"></a><a name="accelerator_view__get_is_debug"></a>get_is_debug 

返回一个布尔值，该值指示 accelerator_view 对象是否为广泛的错误报告启用了调试层。  
  
### <a name="syntax"></a>语法  
  
```  
bool get_is_debug() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个布尔值，指示 `accelerator_view` 对象是否为广泛的错误报告启用了调试层。  

## <a name="a-nameacceleratorviewgetqueuingmodea-getqueuingmode"></a><a name="accelerator_view__get_queuing_mode"></a>get_queuing_mode 

返回 accelerator_view 对象的排队模式。  
  
### <a name="syntax"></a>语法  
  
```  
queuing_mode get_queuing_mode() const;  
```  
  
### <a name="return-value"></a>返回值  
 `accelerator_view` 对象的排队模式。  
  
## <a name="a-nameacceleratorviewgetversiona-getversion"></a><a name="accelerator_view__get_version"></a>get_version 

返回 accelerator_view 的版本。  
  
### <a name="syntax"></a>语法  
  
```  
unsigned int get_version() const;  
```  
  
### <a name="return-value"></a>返回值  
 版本`accelerator_view`。  
  
## <a name="a-nameacceleratorviewisautoselectiona-isautoselection"></a><a name="accelerator_view__is_auto_selection"></a>is_auto_selection 

获取一个布尔值，该值指示是否 accelerator_view 传递给时，运行时将自动选择适当的加速器[parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each)。  
  
### <a name="syntax"></a>语法  
  
```  
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;  
```  
  
## <a name="a-nameacceleratorviewisdebuga-isdebug"></a><a name="accelerator_view__is_debug"></a>is_debug 

获取一个布尔值，该值指示 accelerator_view 对象是否为广泛的错误报告启用了调试层。  
  
### <a name="syntax"></a>语法  
  
```  
__declspec(property(get= get_is_debug)) bool is_debug;  
```  
  
## <a name="a-nameacceleratorviewoperatorneqa-operator"></a><a name="accelerator_view__operator_neq"></a>运算符 ！ = 

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
  
## <a name="a-nameacceleratorviewoperatoreqa-operator"></a><a name="accelerator_view__operator_eq"></a>运算符 = 

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
  
## <a name="a-nameacceleratorviewoperatoreqeqa-operator"></a><a name="accelerator_view__operator_eq_eq"></a>运算符 = = 

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
  
## <a name="a-nameacceleratorviewqueuingmodea-queuingmode"></a><a name="accelerator_view__queuing_mode"></a>queuing_mode 

获取 accelerator_view 对象排队模式。  
  
### <a name="syntax"></a>语法  
  
```  
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;  
```  
  
## <a name="a-nameacceleratorviewversiona-version"></a><a name="accelerator_view__version"></a>版本 

获取 accelerator_view 的版本。  
  
### <a name="syntax"></a>语法  
  
```  
__declspec(property(get= get_version)) unsigned int version;  
```  
  
## <a name="a-nameacceleratorviewwaita-wait"></a><a name="accelerator_view__wait"></a>等待 

等待所有命令提交给 accelerator_view 对象都完成。  
  
### <a name="syntax"></a>语法  
  
```  
void wait();  
```  
  
#### <a name="return-value"></a>返回值  
 返回 `void`。  
  
#### <a name="remarks"></a>备注  
 如果[queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode)是`immediate`，此方法会立即返回而不会阻止。  
  
##  <a name="a-namedtora-acceleratorview"></a><a name="dtor"></a>~ accelerator_view 

 销毁 accelerator_view 对象。  
  
#### <a name="syntax"></a>语法  
  
```  
~accelerator_view();  
```  
  
### <a name="return-value"></a>返回值  
  
 
## <a name="see-also"></a>另请参阅  
 [并发 Namespace (c + + AMP)](concurrency-namespace-cpp-amp.md)

