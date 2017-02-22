---
title: "ComPtr 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Microsoft::WRL::ComPtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ComPtr 类"
ms.assetid: a6551902-6819-478a-8df7-b6f312ab1fb0
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# ComPtr 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

创建表示模板参数指定的接口的*智能指针*类型。 ComPtr 会自动维护基础接口指针的引用计数，并在引用计数变为零时释放接口。  
  
## 语法  
  
```  
template <  
   typename T  
>  
class ComPtr;  
  
template<  
   class U  
>  
friend class ComPtr;  
```  
  
#### 参数  
 `T`  
 ComPtr 代表的接口。  
  
 `U`  
 当前 ComPtr 为其友元的类。 （使用此参数的模板受到保护。）  
  
## 备注  
 ComPtr\<\> 声明表示基础接口指针的类型。 使用 ComPtr\<\> 声明一个变量，然后使用箭头成员访问运算符 \(`->`\) 访问接口成员函数。  
  
 有关智能指针的详细信息，请参阅 MSDN 库中 [COM Coding Practices](http://msdn.microsoft.com/zh-cn/76aca556-b4d6-4e67-a2a3-4439900f0c39)主题的“COM 智能指针”部分。  
  
## 成员  
  
### 公共 Typedef  
  
|名称|说明|  
|--------|--------|  
|`InterfaceType`|`T` 模板参数指定的类型的同义词。|  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[ComPtr::ComPtr 构造函数](../windows/comptr-comptr-constructor.md)|初始化 ComPtr 类的新实例。 重载提供默认、复制、移动和转换构造函数。|  
|[ComPtr::~ComPtr 析构函数](../windows/comptr-tilde-comptr-destructor.md)|取消初始化 ComPtr 的实例。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[ComPtr::As 方法](../windows/comptr-as-method.md)|返回表示由指定模板参数标识的接口的 ComPtr 对象。|  
|[ComPtr::AsIID 方法](../windows/comptr-asiid-method.md)|返回表示由指定接口 ID 标识的接口的 ComPtr 对象。|  
|[ComPtr::AsWeak 方法](../windows/comptr-asweak-method.md)|检索对当前对象的弱引用。|  
|[ComPtr::Attach 方法](../windows/comptr-attach-method.md)|将此 ComPtr 与由当前模板类型参数指定的接口类型相关联。|  
|[ComPtr::CopyTo 方法](../windows/comptr-copyto-method.md)|将与此 ComPtr 关联的当前或指定接口复制到指定输出指针。|  
|[ComPtr::Detach 方法](../windows/comptr-detach-method.md)|从此 ComPtr 所表示的接口取消关联它。|  
|[ComPtr::Get 方法](../windows/comptr-get-method.md)|检索指向与此 ComPtr 相关联的接口。|  
|[ComPtr::GetAddressOf 方法](../windows/comptr-getaddressof-method.md)|检索 [ptr\_](../windows/comptr-ptr-data-member.md) 数据成员的地址，其中包含指向此 ComPtr 所表示接口的指针。|  
|[ComPtr::ReleaseAndGetAddressOf 方法](../windows/comptr-releaseandgetaddressof-method.md)|释放与此 ComPtr 关联的接口，然后检索 [ptr\_](../windows/comptr-ptr-data-member.md) 数据成员的地址，其中包含指向已释放接口的指针。|  
|[ComPtr::Reset](../windows/comptr-reset.md)|释放所有指向与此 ComPtr 相关联的接口的指针的引用。|  
|[ComPtr::Swap 方法](../windows/comptr-swap-method.md)|交换由当前 ComPtr 托管的接口与由指定 ComPtr 托管的接口。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[ComPtr::InternalAddRef 方法](../windows/comptr-internaladdref-method.md)|递增与此 ComPtr 关联的接口的引用计数。|  
|[ComPtr::InternalRelease 方法](../windows/comptr-internalrelease-method.md)|对与此 ComPtr 关联的接口执行 COM 释放操作。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[ComPtr::operator Microsoft::WRL::Details::BoolType 运算符](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md)|指示 ComPtr 是否托管接口的对象生存期。|  
|[ComPtr::operator& 运算符](../windows/comptr-operator-ampersand-operator.md)|检索当前 ComPtr 的地址。|  
|[ComPtr::operator\= 运算符](../windows/comptr-operator-assign-operator.md)|为当前 ComPtr 赋值。|  
|[ComPtr::operator\-\> 运算符](../windows/comptr-operator-arrow-operator.md)|检索指向当前模板参数所指定类型的指针。|  
|[ComPtr::operator\=\= 运算符](../windows/comptr-operator-equality-operator.md)|指示两个 ComPtr 对象是否相等。|  
|[ComPtr::operator\!\= 运算符](../windows/comptr-operator-inequality-operator.md)|指示两个 ComPtr 对象是否不相等。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[ComPtr::ptr\_ 数据成员](../windows/comptr-ptr-data-member.md)|包含指向与此 ComPtr 相关联且由其托管的接口。|  
  
## 继承层次结构  
 `ComPtr`  
  
## 要求  
 **标头：**client.h  
  
 **命名空间：**Microsoft::WRL  
  
## 请参阅  
 [Microsoft::WRL 命名空间](../windows/microsoft-wrl-namespace.md)