---
title: WeakReference 类 1 |Microsoft Docs
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
ms.openlocfilehash: 78b9a62838508c2e97bdd04f56778a622343e6f1
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40012285"
---
# <a name="weakreference-class1"></a>WeakReference 类 1
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```cpp  
class WeakReference;  
```  
  
## <a name="remarks"></a>备注  
 表示*弱引用*可以用于 Windows 运行时或经典 com。 弱引用表示可能可访问或可能不可访问的对象。  
  
 一个**WeakReference**对象维护*强引用*，这是指向对象的指针和一个*强引用计数*，这是强的副本数已通过分发的引用`Resolve()`方法。 非零值的强引用计数时，强引用有效且该对象是可访问。 当强引用计数变为零时，强引用无效，该对象是不可访问。  
  
 一个**WeakReference**对象通常用于表示由外部线程或应用程序控制其存在性的对象。 例如，构造**WeakReference**中对文件对象的引用的对象。 文件打开时，强引用有效。 但文件关闭时，强引用无效。  
  
 **WeakReference**是线程安全的方法。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[WeakReference::WeakReference 构造函数](../windows/weakreference-weakreference-constructor.md)|初始化的新实例**WeakReference**类。|  
|[WeakReference::~WeakReference 析构函数](../windows/weakreference-tilde-weakreference-destructor.md)|取消初始化 （销毁） 的当前实例**WeakReference**类。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[WeakReference::DecrementStrongReference 方法](../windows/weakreference-decrementstrongreference-method.md)|当前的强引用计数的递减**WeakReference**对象。|  
|[WeakReference::IncrementStrongReference 方法](../windows/weakreference-incrementstrongreference-method.md)|当前的强引用计数递增**WeakReference**对象。|  
|[WeakReference::Resolve 方法](../windows/weakreference-resolve-method.md)|将指定的指针设置为当前的强引用值，如果强引用计数不为零。|  
|[WeakReference::SetUnknown 方法](../windows/weakreference-setunknown-method.md)|设置当前的强引用**WeakReference**对象与指定的接口指针。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `WeakReference`  
  
## <a name="requirements"></a>要求  
 **标头：** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)