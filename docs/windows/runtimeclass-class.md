---
title: "RuntimeClass 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::RuntimeClass
dev_langs: C++
helpviewer_keywords: RuntimeClass class
ms.assetid: d52f9d1a-98e5-41f2-a143-8fb629dd0727
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e757712b360ff3ed4de12d8236c75a691a1f0c7c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="runtimeclass-class"></a>RuntimeClass 类
表示继承指定数量的接口的实例化类，并提供指定 Windows 运行时、经典 COM 和弱引用支持。  
  
 通常派生从你 WRL 类型`RuntimeClass`因为此类实现`AddRef`， `Release`，和`QueryInterface`，并可帮助管理模块的总体引用计数。  
  
## <a name="syntax"></a>语法  
  
```  
template <  
   typename I0,  
   typename I1 = Details::Nil,  
   typename I2 = Details::Nil,  
   typename I3 = Details::Nil,  
   typename I4 = Details::Nil,  
   typename I5 = Details::Nil,  
   typename I6 = Details::Nil,  
   typename I7 = Details::Nil,  
   typename I8 = Details::Nil,  
   typename I9 = Details::Nil  
>  
class RuntimeClass : public Details::RuntimeClass<typename Details::InterfaceListHelper<I0, I1, I2, I3, I4, I5, I6, I7, I8, I9>::TypeT, RuntimeClassFlags<WinRt>>;  
  
template <  
   unsigned int classFlags,  
   typename I0,  
   typename I1,  
   typename I2,  
   typename I3,  
   typename I4,  
   typename I5,  
   typename I6,  
   typename I7,  
   typename I8  
>  
class RuntimeClass<RuntimeClassFlags<classFlags>, I0, I1, I2, I3, I4, I5, I6, I7, I8> : public Details::RuntimeClass<typename Details::InterfaceListHelper<I0, I1, I2, I3, I4, I5, I6, I7, I8>::TypeT, RuntimeClassFlags<classFlags> >;  
```  
  
#### <a name="parameters"></a>参数  
 `I0`  
 第零个接口 id。 （必需）  
  
 `I1`  
 第一个接口 id。 （可选）  
  
 `I2`  
 第二个接口 id。 （可选）  
  
 `I3`  
 第三个接口 id。 （可选）  
  
 `I4`  
 第四个接口 id。 （可选）  
  
 `I5`  
 第五个接口 id。 （可选）  
  
 `I6`  
 第六个接口 id。 （可选）  
  
 `I7`  
 第七个接口 id。 （可选）  
  
 `I8`  
 第八个接口 id。 （可选）  
  
 `I9`  
 第九个接口 id。 （可选）  
  
 `classFlags`  
 一个或多个组合[RuntimeClassType](../windows/runtimeclasstype-enumeration.md)枚举值。  `__WRL_CONFIGURATION_LEGACY__`可以定义宏，若要更改项目中的所有运行时类的 classFlags 的默认值。 如果定义，则 RuntimeClass 实例进行非敏捷 dy 默认。 未定义时，RuntimeClass 实例都是敏捷的默认值。 若要避免多义性始终指定 RuntimeClassType::FtmBase 或 RuntimeClassType::InhibitFtmBase。
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[RuntimeClass::RuntimeClass 构造函数](../windows/runtimeclass-runtimeclass-constructor.md)|初始化 RuntimeClass 类的当前实例。|  
|[RuntimeClass::~RuntimeClass 析构函数](../windows/runtimeclass-tilde-runtimeclass-destructor.md)|取消初始化 RuntimeClass 类的当前实例。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `I0`  
  
 `ChainInterfaces`  
  
 `I0`  
  
 `RuntimeClassBase`  
  
 `ImplementsHelper`  
  
 `DontUseNewUseMake`  
  
 `RuntimeClassFlags`  
  
 `RuntimeClassBaseT`  
  
 `RuntimeClass`  
  
 `RuntimeClass`  
  
## <a name="requirements"></a>要求  
 **标头：** implements.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>另请参阅  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)
