---
title: "ComPtrRefBase 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Microsoft::WRL::Details::ComPtrRefBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ComPtrRefBase 类"
ms.assetid: 6d344c1a-cc13-4a3f-8a0d-f167ccb9348f
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# ComPtrRefBase 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
template <  
   typename T  
>  
class ComPtrRefBase;  
```  
  
#### 参数  
 `T`  
 [ComPtr\<T\>](../windows/comptr-class.md) 类型或从它，ComPtr 表示的接口没有派生的。  
  
## 备注  
 [ComPtrRef](../windows/comptrref-class.md) 表示类的基类。  
  
## 成员  
  
### 公共 Typedef  
  
|名称|说明|  
|--------|--------|  
|`InterfaceType`|表示模板参数的 `T`同义词。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[ComPtrRefBase::operator IInspectable\*\* 运算符](../windows/comptrrefbase-operator-iinspectable-star-star-operator.md)|模拟当前数据成员设置为指针对 [ptr\_](../windows/comptrrefbase-ptr-data-member.md) 指针对 IInspectable 接口中。|  
|[ComPtrRefBase::operator IUnknown\*\* 运算符](../windows/comptrrefbase-operator-iunknown-star-star-operator.md)|模拟当前数据成员设置为指针对 [ptr\_](../windows/comptrrefbase-ptr-data-member.md) 指针对 IUnknown 接口中。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[ComPtrRefBase::ptr\_ 数据成员](../windows/comptrrefbase-ptr-data-member.md)|为当前模板参数指定的类型的指针。|  
  
## 继承层次结构  
 `ComPtrRefBase`  
  
## 要求  
 **标头：**client.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)