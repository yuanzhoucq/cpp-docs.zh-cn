---
title: "HString 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString
dev_langs:
- C++
ms.assetid: 6709dd2e-8d72-4675-8ec7-1baa7d71854d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3e8d66f134eef5f2ecb75b30fd68874418dbc49d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="hstring-class"></a>HString 类
用于管理 HSTRING 使用 RAII 模式的生存期的帮助器类。
  
## <a name="syntax"></a>语法  
  
```cpp  
class HString;  
```  
  
## <a name="remarks"></a>备注  
 Windows 运行时提供访问权限通过 HSTRING 句柄的字符串。 HString 类提供易于使用的功能和运算符来简化使用 HSTRING 句柄。 此类可以处理它拥有通过 RAII 模式 HSTRING 的生存期。 
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[HString::HString 构造函数](../windows/hstring-hstring-constructor.md)|初始化 HString 类的新实例。|  
|[HString::~HString 析构函数](../windows/hstring-tilde-hstring-destructor.md)|销毁 HString 类的当前实例。|  
  
### <a name="members"></a>成员  
  
|名称|描述|  
|----------|-----------------|  
|[HString::Set 方法](../windows/hstring-set-method.md)|将当前 HString 对象的值设置为指定的宽字符字符串或 HString 参数。|  
|[HString::Attach 方法](../windows/hstring-attach-method.md)|将指定的 HString 对象与当前 HString 对象相关联。|  
|[HString::CopyTo 方法](../windows/hstring-copyto-method.md)|复制当前 HString 对象 HSTRING 对象。|  
|[HString::Detach 方法](../windows/hstring-detach-method.md)|解除关联中其基础值的指定的 HString 对象。|  
|[HString::GetAddressOf 方法](../windows/hstring-getaddressof-method.md)|检索指向基础 HSTRING 句柄的指针。|  
|[HString::Get 方法](../windows/hstring-get-method.md)|检索基础 HSTRING 句柄的值。|  
|[HString::Release 方法](../windows/hstring-release-method.md)|删除的基础字符串值，并初始化为空值的当前 HString 对象。|  
|[HString::MakeReference 方法](../windows/hstring-makereference-method.md)|从指定的字符串参数创建 HStringReference 对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[HString::Operator= 运算符](../windows/hstring-operator-assign-operator.md)|将另一个 HString 对象的值移到当前 HString 对象。|  
|[HString::Operator== 运算符](../windows/hstring-operator-equality-operator.md)|指示两个参数是否相等。|  
|[HString::Operator!= 运算符](../windows/hstring-operator-inequality-operator.md)|指示两个参数是否不相等。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `HString`  
  
## <a name="requirements"></a>惠?  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Wrappers 命名空间](../windows/microsoft-wrl-wrappers-namespace.md)