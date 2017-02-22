---
title: "HStringReference 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HStringReference"
dev_langs: 
  - "C++"
ms.assetid: 9bf823b1-17eb-4ac4-8c5d-27d27c7a4150
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# HStringReference 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示从现有字符串创建的 HSTRING。  
  
## 语法  
  
```cpp  
class HStringReference;  
```  
  
## 备注  
 新 HSTRING 中的支持缓冲区的生存期不受 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 管理。  调用方分配堆栈帧的源字符串以避免堆分配并消除内存泄漏的风险。  此外，调用方必须确保源字符串在附加 HSTRING 的生存期内保持不变。  有关详细信息，请参阅 [WindowsCreateStringReference function](http://msdn.microsoft.com/zh-cn/0361bb7e-da49-4289-a93e-de7aab8712ac)。  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[HStringReference::HStringReference 构造函数](../windows/hstringreference-hstringreference-constructor.md)|初始化 HStringReference 类的新实例。|  
  
### 成员  
  
|成员|描述|  
|--------|--------|  
|[HStringReference::CopyTo 方法](../windows/hstringreference-copyto-method.md)|将当前 HStringReference 对象复制到 HSTRING 对象。|  
|[HStringReference::Get 方法](../windows/hstringreference-get-method.md)|检索基础 HSTRING 句柄的值。|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[HStringReference::Operator\= 运算符](../windows/hstringreference-operator-assign-operator.md)|将另一 HStringReference 对象的值移动至当前 HStringReference 对象。|  
|[HStringReference::Operator\=\= 运算符](../windows/hstringreference-operator-equality-operator.md)|指示两个参数是否相等。|  
|[HStringReference::Operator\!\= 运算符](../windows/hstringreference-operator-inequality-operator.md)|指示两个参数是否不相等。|  
  
## 继承层次结构  
 `HStringReference`  
  
## 要求  
 **头文件：**corewrappers.h  
  
 **命名空间：**Microsoft::WRL::Wrappers  
  
## 请参阅  
 [Microsoft::WRL::Wrappers 命名空间](../windows/microsoft-wrl-wrappers-namespace.md)