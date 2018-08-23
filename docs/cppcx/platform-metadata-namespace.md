---
title: 'Platform:: metadata Namespace |Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Metadata
dev_langs:
- C++
helpviewer_keywords:
- Platform::Metadata Namespace
ms.assetid: e3e114d8-a4b0-47f0-865a-9ce9d7212e86
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f1a755314adec83e8853c2c29d9c9d9bb363575b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607801"
---
# <a name="platformmetadata-namespace"></a>Platform::Metadata 命名空间
此命名空间包含修改类型声明的特性。  
  
## <a name="syntax"></a>语法  
  
```cpp  
  
namespace Platform {  
   namespace Metadata {  
}}  
```  
  
### <a name="members"></a>成员  
 虽然此命名空间供内部使用，但是浏览器可以显示此命名空间的以下成员。  
  
|name|备注|  
|----------|------------|  
|特性|特性的基类。|  
|[Platform::Metadata::DefaultMemberAttribute 特性](../cppcx/platform-metadata-defaultmemberattribute-attribute.md)|指示首选函数以在几个可能的重载函数中调用。|  
|[Platform::Metadata::FlagsAttribute 特性](../cppcx/platform-metadata-flagsattribute-attribute.md)标记|声明枚举为位域的枚举。<br /><br /> 下面的示例演示如何将枚举应用于 `Flags` 特性。<br /><br /> `[Flags] enum class MyEnumeration { enumA = 1, enumB = 2, enumC = 3}`|  
|[Platform::Metadata::RuntimeClassNameAttribute](../cppcx/platform-metadata-runtimeclassname.md)|确保私有 ref 类具有一个有效的运行时类名称。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `Platform`  
  
### <a name="requirements"></a>要求  
 **元数据：** platform.winmd  
  
 **命名空间：** Platform::Metadata  
  
## <a name="see-also"></a>请参阅  
 [平台 Namespace](platform-namespace-c-cx.md)