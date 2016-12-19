---
title: "HString 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HString"
dev_langs: 
  - "C++"
ms.assetid: 6709dd2e-8d72-4675-8ec7-1baa7d71854d
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HString 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

为处理 HSTRING 句柄提供支持。  
  
## 语法  
  
```cpp  
class HString;  
```  
  
## 备注  
 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 通过 HSTRING 句柄提供字符串的访问权限。  HString 类提供便利函数和运算符以简化使用 HSTRING 句柄。  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[HString::HString 构造函数](../windows/hstring-hstring-constructor.md)|初始化 HString 类的新实例。|  
|[HString::~HString 析构函数](../windows/hstring-tilde-hstring-destructor.md)|销毁 HString 类的当前实例。|  
  
### 成员  
  
|名称|描述|  
|--------|--------|  
|[HString::Set 方法](../windows/hstring-set-method.md)|将当前 HString 对象的值设置为指定的宽字符串或 HString 参数。|  
|[HString::Attach 方法](../windows/hstring-attach-method.md)|将指定的 HString 对象与当前的 HString 对象关联。|  
|[HString::CopyTo 方法](../windows/hstring-copyto-method.md)|将当前 HString 对象复制到 HSTRING 对象。|  
|[HString::Detach 方法](../windows/hstring-detach-method.md)|将指定的 HString 对象从其基础值分离。|  
|[HString::GetAddressOf 方法](../windows/hstring-getaddressof-method.md)|检索基础 HSTRING 句柄的指针。|  
|[HString::Get 方法](../windows/hstring-get-method.md)|检索基础 HSTRING 句柄的值。|  
|[HString::Release 方法](../windows/hstring-release-method.md)|删除基础字符串值，并将当前 HString 对象初始化为空值。|  
|[HString::MakeReference 方法](../windows/hstring-makereference-method.md)|从指定的字符串参数创建 HStringReference 对象。|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[HString::Operator\= 运算符](../windows/hstring-operator-assign-operator.md)|将另一 HString 对象的值移动至当前 HString 对象。|  
|[HString::Operator\=\= 运算符](../windows/hstring-operator-equality-operator.md)|指示两个参数是否相等。|  
|[HString::Operator\!\= 运算符](../windows/hstring-operator-inequality-operator.md)|指示两个参数是否不相等。|  
  
## 继承层次结构  
 `HString`  
  
## 要求  
 **头文件：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [Microsoft::WRL::Wrappers 命名空间](../windows/microsoft-wrl-wrappers-namespace.md)