---
title: "AsyncBase 类 | Microsoft Docs"
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
  - "async/Microsoft::WRL::AsyncBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AsyncBase 类"
ms.assetid: 64259b9b-f427-4ffd-a611-e7a2f82362b2
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AsyncBase 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

实现 Windows 时运行异步状态机。  
  
## 语法  
  
```  
  
template <  
   typename TComplete,  
   typename TProgress = Details::Nil,  
   AsyncResultType resultType = SingleResult  
>  
class AsyncBase : public AsyncBase< TComplete, Details::Nil, resultType >;  
  
template <  
   typename TComplete,  
   AsyncResultType resultType  
>  
class AsyncBase< TComplete, Details::Nil, resultType > : public Microsoft::WRL::Implements< IAsyncInfo >;  
```  
  
#### 参数  
 `TComplete`  
 调用的事件处理程序，以便在异步操作完成。  
  
 `TProgress`  
 调用的事件处理程序，当中正在运行的异步操作的当前报告操作进度。  
  
 `resultType`  
 必须是 [](../windows/asyncresulttype-enumeration.md "AsyncResultType Enumeration") 枚举中的值之一。  默认情况下，SingleResult。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[AsyncBase::AsyncBase 构造函数](../windows/asyncbase-asyncbase-constructor.md)|初始化AsyncBase类的实例。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[AsyncBase::Cancel 方法](../windows/asyncbase-cancel-method.md)|这是一个异步操作。|  
|[AsyncBase::Close 方法](../windows/asyncbase-close-method.md)|结束异步操作。|  
|[AsyncBase::FireCompletion 方法](../windows/asyncbase-firecompletion-method.md)|调用完成事件处理程序内部委托或重置进度。|  
|[AsyncBase::FireProgress 方法](../windows/asyncbase-fireprogress-method.md)|调用活动进程事件处理程序。|  
|[AsyncBase::get\_ErrorCode 方法](../windows/asyncbase-get-errorcode-method.md)|检索当前异步操作中的错误代码。|  
|[AsyncBase::get\_Id 方法](../windows/asyncbase-get-id-method.md)|检索异步操作的句柄。|  
|[AsyncBase::get\_Status 方法](../windows/asyncbase-get-status-method.md)|检索一个枚举值，它指示工作流同步操作的状态。|  
|[AsyncBase::GetOnComplete 方法](../windows/asyncbase-getoncomplete-method.md)|复制当前进度事件处理程序的地址为指定的变量。|  
|[AsyncBase::GetOnProgress 方法](../windows/asyncbase-getonprogress-method.md)|复制当前进度事件处理程序的地址为指定的变量。|  
|[AsyncBase::put\_Id 方法](../windows/asyncbase-put-id-method.md)|检索异步操作的句柄。|  
|[AsyncBase::PutOnComplete 方法](../windows/asyncbase-putoncomplete-method.md)|设置完成事件处理程序的地址为指定值。|  
|[AsyncBase::PutOnProgress 方法](../windows/asyncbase-putonprogress-method.md)|设置完成事件处理程序的地址为指定值。|  
|[AsyncBase::Start 方法](../windows/asyncbase-start-method.md)|开始异步操作。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[AsyncBase::CheckValidStateForDelegateCall 方法](../windows/asyncbase-checkvalidstatefordelegatecall-method.md)|测试委托属性是否可在当前异步状态修改。|  
|[AsyncBase::CheckValidStateForResultsCall 方法](../windows/asyncbase-checkvalidstateforresultscall-method.md)|研究异步操作的结果是否可以在当前异步状态的集合。|  
|[AsyncBase::ContinueAsyncOperation 方法](../windows/asyncbase-continueasyncoperation-method.md)|确定异步操作是否应继续处理还是应暂停。|  
|[AsyncBase::CurrentStatus 方法](../windows/asyncbase-currentstatus-method.md)|检查当前异步操作的状态。|  
|[AsyncBase::ErrorCode 方法](../windows/asyncbase-errorcode-method.md)|检索当前异步操作中的错误代码。|  
|[AsyncBase::OnCancel 方法](../windows/asyncbase-oncancel-method.md)|在派生类中重写时，取消同步操作。|  
|[AsyncBase::OnClose 方法](../windows/asyncbase-onclose-method.md)|在派生类中重写时，结束异步刷新操作。|  
|[AsyncBase::OnStart 方法](../windows/asyncbase-onstart-method.md)|在派生类中重写时，开始异步刷新操作。|  
|[AsyncBase::TryTransitionToCompleted 方法](../windows/asyncbase-trytransitiontocompleted-method.md)|指示当前异步操作是否已完成。|  
|[AsyncBase::TryTransitionToError 方法](../windows/asyncbase-trytransitiontoerror-method.md)|指示指定的错误代码是否能够修改内部错误状态。|  
  
## 继承层次结构  
 `AsyncBase`  
  
 `AsyncBase`  
  
## 要求  
 **页眉：**async.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [Microsoft::WRL 命名空间](../windows/microsoft-wrl-namespace.md)