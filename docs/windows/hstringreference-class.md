---
title: HStringReference 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference
dev_langs:
- C++
ms.assetid: 9bf823b1-17eb-4ac4-8c5d-27d27c7a4150
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 90e94471fe114eafec91a19ddad5d47ce39a8de7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="hstringreference-class"></a>HStringReference 类
表示 HSTRING 创建从现有字符串。  
  
## <a name="syntax"></a>语法  
  
```cpp  
class HStringReference;  
```  
  
## <a name="remarks"></a>备注  
 不由 Windows 运行时管理中新 HSTRING 后备缓冲区的生存期。 调用方分配的源字符串，以避免堆分配并消除了内存泄漏的风险的堆栈帧上。 此外，调用方必须确保源字符串附加 HSTRING 的生存期内保持不变。 有关详细信息，请参阅[WindowsCreateStringReference 函数](http://msdn.microsoft.com/en-us/0361bb7e-da49-4289-a93e-de7aab8712ac)。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[HStringReference::HStringReference 构造函数](../windows/hstringreference-hstringreference-constructor.md)|初始化 HStringReference 类的新实例。|  
  
### <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|[HStringReference::CopyTo 方法](../windows/hstringreference-copyto-method.md)|复制当前 HStringReference 对象 HSTRING 对象。|  
|[HStringReference::Get 方法](../windows/hstringreference-get-method.md)|检索基础 HSTRING 句柄的值。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[HStringReference::Operator= 运算符](../windows/hstringreference-operator-assign-operator.md)|将另一 HStringReference 对象的值移到当前 HStringReference 对象。|  
|[HStringReference::Operator== 运算符](../windows/hstringreference-operator-equality-operator.md)|指示两个参数是否相等。|  
|[HStringReference::Operator!= 运算符](../windows/hstringreference-operator-inequality-operator.md)|指示两个参数是否不相等。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `HStringReference`  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Wrappers 命名空间](../windows/microsoft-wrl-wrappers-namespace.md)