---
title: "CreateClassFactory 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Details::CreateClassFactory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateClassFactory 函数"
ms.assetid: 772d5d1b-8872-4745-81ca-521a39564713
caps.latest.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 2
---
# CreateClassFactory 函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

创建生成指定的类的实例中的工厂。  
  
## 语法  
  
```cpp  
  
template<typename Factory>  
inline HRESULT STDMETHODCALLTYPE CreateClassFactory(  
   _In_ unsigned int *flags,   
   _In_ const CreatorMap* entry,   
   REFIID riid,   
   _Outptr_ IUnknown **ppFactory  
) throw();  
  
```  
  
#### 参数  
 `flags`  
 一个或多个 [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) 枚举值的组合。  
  
 `entry`  
 包含初始化和注册信息 `riid`参数设置为 [CreatorMap](../windows/creatormap-structure.md) 的指针。  
  
 `riid`  
 对接口 ID. 的引用  
  
 `ppFactory`  
 如果该操作成功完成，对类工厂的指针。  
  
## 返回值  
 S\_OK，如果成功；否则，一错误的 HRESULT。  
  
## 备注  
 如果模板参数从 `Factory` 接口对象，不是派生断言错误发出。  
  
## 要求  
 **标头:** module.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [Microsoft::WRL::Wrappers::Details 命名空间](../windows/microsoft-wrl-wrappers-details-namespace.md)