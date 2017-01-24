---
title: "InterfaceTraits 结构 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::Details::InterfaceTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "InterfaceTraits 结构"
ms.assetid: ede0c284-19a7-4892-9738-ff3da4923d0a
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# InterfaceTraits 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL基础结构，不应在代码中直接使用。  
  
## 语法  
  
```  
template<  
   typename I0  
>  
struct __declspec(novtable) InterfaceTraits;  
  
template<  
   typename CloakedType  
>  
struct __declspec(novtable) InterfaceTraits<CloakedIid<CloakedType>>;  
  
template<>  
struct __declspec(novtable) InterfaceTraits<Nil>;  
```  
  
#### 参数  
 `I0`  
 接口名。  
  
 `CloakedType`  
 对于 RuntimeClass、实现和 ChainInterfaces，在不支持的接口 ID 列表的接口。  
  
## 备注  
 实现接口的公共特性。  
  
 第二个模板为掩蔽的接口的专用化。  第三个空模板为参数的专用化。  
  
## 成员  
  
### 公共 Typedef  
  
|名称|说明|  
|--------|--------|  
|`Base`|模板参数 `I0`的同义词。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[InterfaceTraits::CanCastTo 方法](../windows/interfacetraits-cancastto-method.md)|指示指定的指针是否可以转换到 `Base`的指针。|  
|[InterfaceTraits::CastToBase 方法](../windows/interfacetraits-casttobase-method.md)|转换指定的指针到指向 `Base` 的指针。|  
|[InterfaceTraits::CastToUnknown 方法](../windows/interfacetraits-casttounknown-method.md)|转换指定的指针到指向IUnknown的指针。|  
|[InterfaceTraits::FillArrayWithIid 方法](../windows/interfacetraits-fillarraywithiid-method.md)|`Base` 接口 ID 分配给索引参数指定数组的元素。|  
|[InterfaceTraits::Verify 方法](../windows/interfacetraits-verify-method.md)|基本验证正确派生。|  
  
### 公共常量  
  
|名称|说明|  
|--------|--------|  
|[InterfaceTraits::IidCount 常量](../windows/interfacetraits-iidcount-constant.md)|包含接口 ID 的数量与当前 InterfaceTraits 对象。|  
  
## 继承层次结构  
 `InterfaceTraits`  
  
## 要求  
 **头文件：**implements.h  
  
 Microsoft::WRL::Details**命名空间:**  
  
## 请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)