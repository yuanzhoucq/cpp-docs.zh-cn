---
title: "ComPtrRef 类 | Microsoft Docs"
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
  - "client/Microsoft::WRL::Details::ComPtrRef"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ComPtrRef 类"
ms.assetid: d6bdfd20-e977-45b4-9ac1-1b8efbdb77de
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtrRef 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
template <  
   typename T  
>  
class ComPtrRef : public ComPtrRefBase<T>;  
```  
  
#### 参数  
 `T`  
 [ComPtr\<T\>](../windows/comptr-class.md) 类型或从它，ComPtr 表示的接口没有派生的。  
  
## 备注  
 表示对类型 ComPtr\<T\>对象的引用。  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[ComPtrRef::ComPtrRef 构造函数](../windows/comptrref-comptrref-constructor.md)|初始化 ComPtrRef 类的新实例。指定的指针到另一 ComPtrRef 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[ComPtrRef::GetAddressOf 方法](../windows/comptrref-getaddressof-method.md)|检索指向的地址赋给当前 ComPtrRef 表示对象的接口。|  
|[ComPtrRef::ReleaseAndGetAddressOf 方法](../windows/comptrref-releaseandgetaddressof-method.md)|删除当前 ComPtrRef 对象并返回指针的指针，指向由 ComPtrRef 对象表示的接口。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[ComPtrRef::operator InterfaceType\*\* 运算符](../windows/comptrref-operator-interfacetype-star-star-operator.md)|删除当前 ComPtrRef 对象并返回指针的指针，指向由 ComPtrRef 对象表示的接口。|  
|[ComPtrRef::operator T\* 运算符](../windows/comptrref-operator-t-star-operator.md)|返回当前 ComPtrRef [ptr\_](../windows/comptrrefbase-ptr-data-member.md) 对象的数据成员的值。|  
|[ComPtrRef::operator void\*\* 运算符](../windows/comptrref-operator-void-star-star-operator.md)|删除当前 ComPtrRef 对象，指向 ComPtrRef 转换由对象表示为指针对指针对 `void`的接口，然后返回指针转换。|  
|[ComPtrRef::operator\* 运算符](../windows/comptrref-operator-star-operator.md)|检索指向 ComPtrRef 对象表示接口的指针。|  
|[ComPtrRef::operator\=\= 运算符](../windows/comptrref-operator-equality-operator.md)|指示两个ComPtrRef 对象是否不相等。|  
|[ComPtrRef::operator\!\= 运算符](../windows/comptrref-operator-inequality-operator.md)|指示两个ComPtrRef对象是否不相等。|  
  
## 继承层次结构  
 `ComPtrRefBase`  
  
 `ComPtrRef`  
  
## 要求  
 **标头：**client.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)