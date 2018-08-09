---
title: RuntimeClass 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass
dev_langs:
- C++
helpviewer_keywords:
- RuntimeClass class
ms.assetid: d52f9d1a-98e5-41f2-a143-8fb629dd0727
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7f76695cfe3dcad0f5c835577aa4cc9b7cd3ec62
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017638"
---
# <a name="runtimeclass-class"></a>RuntimeClass 类
表示一个 WinRT 或 COM 类，继承的指定的接口并提供指定的 Windows 运行时、 经典 COM 和弱引用支持。  
  
此类提供了 WinRT 和 COM 类，提供的实现的样板实现`QueryInterface`， `AddRef`，`Release`等，管理模块的引用计数和提供的类工厂的支持可激活的对象。
  
## <a name="syntax"></a>语法  
  
```cpp
template <typename ...TInterfaces> class RuntimeClass
template <unsigned int classFlags, typename ...TInterfaces> class RuntimeClass;
```
  
### <a name="parameters"></a>参数  
 *classFlags*  
可选参数。 一个或多个组合[RuntimeClassType](../windows/runtimeclasstype-enumeration.md)枚举值。 `__WRL_CONFIGURATION_LEGACY__`可以定义宏，若要更改的项目中的所有运行时类 classFlags 的默认值。 如果定义，RuntimeClass 实例是默认情况下非敏捷。 未定义时，RuntimeClass 实例是默认情况下敏捷的。 若要避免多义性始终指定`Microsoft::WRL::FtmBase`中`TInterfaces`或`RuntimeClassType::InhibitFtmBase`。 请注意，如果 InhibitFtmBase 和 FtmBase 是同时使用该对象将是敏捷类。
 
 *TInterfaces*  
接口列表中的该对象实现之外`IUnknown`，`IInspectable`或控制的其他接口[RuntimeClassType](../windows/runtimeclasstype-enumeration.md)。 它还可能会列出其他类以值得注意的是派生自`Microsoft::WRL::FtmBase`使对象敏捷，从而使该实现`IMarshal`。
  
## <a name="members"></a>成员  
`RuntimeClassInitialize` 如果初始化该对象的函数的`MakeAndInitialize`模板函数用于构造对象。 如果初始化失败，则返回如果对象已成功初始化，则为 S_OK 或 COM 错误代码。 COM 错误代码传播的返回值作为`MakeAndInitialize`。 请注意，`RuntimeClassInitialize`如果不调用方法`Make`模板函数用于构造对象。

### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[RuntimeClass::RuntimeClass 构造函数](../windows/runtimeclass-runtimeclass-constructor.md)|初始化 RuntimeClass 类的当前实例。|  
|[RuntimeClass::~RuntimeClass 析构函数](../windows/runtimeclass-tilde-runtimeclass-destructor.md)|取消初始化 RuntimeClass 类的当前实例。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
这是实现详细信息。
  
## <a name="requirements"></a>要求  
**标头：** implements.h  
  
**命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)