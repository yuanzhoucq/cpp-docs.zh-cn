---
title: WeakReference Class1 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference
dev_langs:
- C++
helpviewer_keywords:
- WeakReference class
ms.assetid: 3f4c956b-dbbd-49b1-8cfa-9509a9956c97
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a44b992138371ff33a9059990a5ec3e93689c679
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891641"
---
# <a name="weakreference-class1"></a>WeakReference Class1
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
class WeakReference;  
```  
  
## <a name="remarks"></a>备注  
 表示*弱引用*可以与 Windows 运行时或经典 COM 使用 弱引用表示可能可访问或可能不可访问的对象。  
  
 A`WeakReference`对象维护*强引用*，这是指向对象的指针和一个*强引用计数*，即已通过分发强引用的副本数Resolve() 方法中。 非零的强引用计数时，强引用有效并对象是可访问。 当强引用计数变为零时，强引用无效，对象是不可访问。  
  
 WeakReference 对象通常用于表示由外部线程或应用程序控制其存在性的对象。 例如，构造 WeakReference 对象从对文件对象的引用。 文件打开时，强引用有效。 但文件关闭时，强引用无效。  
  
 WeakReference 方法都是线程安全。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[WeakReference::WeakReference 构造函数](../windows/weakreference-weakreference-constructor.md)|初始化 WeakReference 类的新实例。|  
|[WeakReference::~WeakReference 析构函数](../windows/weakreference-tilde-weakreference-destructor.md)|取消初始化 （销毁） WeakReference 类的当前实例。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[WeakReference::DecrementStrongReference 方法](../windows/weakreference-decrementstrongreference-method.md)|递减当前 WeakReference 对象的强引用计数。|  
|[WeakReference::IncrementStrongReference 方法](../windows/weakreference-incrementstrongreference-method.md)|递增当前 WeakReference 对象的强引用计数。|  
|[WeakReference::Resolve 方法](../windows/weakreference-resolve-method.md)|如果强引用计数不为零，请将指定的指针设置为当前的强引用值。|  
|[WeakReference::SetUnknown 方法](../windows/weakreference-setunknown-method.md)|将当前的 WeakReference 对象的强引用设置为指定的接口指针。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `WeakReference`  
  
## <a name="requirements"></a>要求  
 **标头：** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)