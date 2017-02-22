---
title: "FtmBase 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ftm/Microsoft::WRL::FtmBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FtmBase 类"
ms.assetid: 275f3b71-2975-4f92-89e7-d351e96496df
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# FtmBase 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示自由线程封送拆收器对象。  
  
## 语法  
  
```  
  
class FtmBase : public Microsoft::WRL::Implements<  
   Microsoft::WRL::RuntimeClassFlags< WinRtClassicComMix >,   
   Microsoft::WRL::CloakedIid< IMarshal > >;  
```  
  
## 备注  
 有关更多信息，请参见“COM 连接”COM 引用”主题的副主题中的“IMarshal”主题 MSDN Library。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[FtmBase::FtmBase 构造函数](../windows/ftmbase-ftmbase-constructor.md)|初始化 FtmBase 类的新实例。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[FtmBase::CreateGlobalInterfaceTable 方法](../windows/ftmbase-createglobalinterfacetable-method.md)|创建全局表 \(GIT\) 接口。|  
|[FtmBase::DisconnectObject 方法](../windows/ftmbase-disconnectobject-method.md)|优秀释放对对象的任何外部连接。  对象的服务器在关闭之前调用该方法的对象的实现。|  
|[FtmBase::GetMarshalSizeMax 方法](../windows/ftmbase-getmarshalsizemax-method.md)|获取最大限制所需的字节数封送对指定对象指定的接口指针。|  
|[FtmBase::GetUnmarshalClass 方法](../windows/ftmbase-getunmarshalclass-method.md)|获取 COM 用于定位包含对应的代理代码的 DLL 的 CLSID。  COM 加载此 DLL 创建代理未初始化的实例的。|  
|[FtmBase::MarshalInterface 方法](../windows/ftmbase-marshalinterface-method.md)|写入流中需要数据的初始化放到某客户端进程的代理对象。|  
|[FtmBase::ReleaseMarshalData 方法](../windows/ftmbase-releasemarshaldata-method.md)|销毁一个封送的数据包。|  
|[FtmBase::UnmarshalInterface 方法](../windows/ftmbase-unmarshalinterface-method.md)|初始化新生成的代理接口并返回指向该代理。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[FtmBase::marshaller\_ 数据成员](../windows/ftmbase-marshaller-data-member.md)|保留了自由线程封的引用。|  
  
## 继承层次结构  
 `FtmBase`  
  
## 要求  
 **页眉：**ftm.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [Microsoft::WRL 命名空间](../windows/microsoft-wrl-namespace.md)