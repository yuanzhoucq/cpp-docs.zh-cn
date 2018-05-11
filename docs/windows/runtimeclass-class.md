---
title: RuntimeClass 类 |Microsoft 文档
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
ms.openlocfilehash: 26c3542f5bea21d1b705cd3253e6828ff73677df
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="runtimeclass-class"></a>RuntimeClass 类
表示继承指定的接口并提供指定的 Windows 运行时、 经典 COM 和弱引用支持的、 WinRT 或 COM 的类。  
  
此类提供 WinRT 和 COM 的类，提供的实现的样本实现`QueryInterface`， `AddRef`，`Release`等，管理模块的引用计数，并提供的类工厂的支持可激活的对象。
  
## <a name="syntax"></a>语法  
  
```
template <typename ...TInterfaces> class RuntimeClass
template <unsigned int classFlags, typename ...TInterfaces> class RuntimeClass;
```
  
#### <a name="parameters"></a>参数  
 `classFlags`  
可选参数。 一个或多个组合[RuntimeClassType](../windows/runtimeclasstype-enumeration.md)枚举值。 `__WRL_CONFIGURATION_LEGACY__`可以定义宏，若要更改项目中的所有运行时类的 classFlags 的默认值。 如果定义，RuntimeClass 实例是默认情况下非敏捷。 未定义时，RuntimeClass 实例都是敏捷的默认值。 若要避免多义性，始终指定中的 Microsoft::WRL::FtmBase`TInterfaces`或 RuntimeClassType::InhibitFtmBase。 请注意，如果 InhibitFtmBase 和 FtmBase 是这两种使用该对象将是敏捷类。
 
 `TInterfaces`  
超出 IUnknown、 IInspectable 或受其他接口的接口的列表对象实现[RuntimeClassType](../windows/runtimeclasstype-enumeration.md)。 它还可能会列出其他类来从值得注意的是 Microsoft::WRL::FtmBase 派生来使该对象为敏捷，从而使该实现 IMarshal。
  
## <a name="members"></a>成员  
`RuntimeClassInitialize` 一个函数，如果 MakeAndInitialize 模板函数用于构造对象初始化的对象。 如果初始化失败，则返回如果已成功初始化了对象，则为 S_OK 或 COM 错误代码。 COM 错误代码将 MakeAndInitialize 的返回值作为传播。 请注意是否请模板函数用于构造对象不调用 RuntimeClassInitialize 方法。

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
