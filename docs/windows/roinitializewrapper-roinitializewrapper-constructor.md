---
title: 'Roinitializewrapper:: Roinitializewrapper 构造函数 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper
dev_langs:
- C++
ms.assetid: c6f7fb07-14af-4574-9135-cea164607f30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 64f2af40c671760bb8d4e667c209598c46b24665
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="roinitializewrapperroinitializewrapper-constructor"></a>RoInitializeWrapper::RoInitializeWrapper 构造函数
初始化 RoInitializeWrapper 类的新实例。  
  
## <a name="syntax"></a>语法  
  
```cpp  
RoInitializeWrapper(   RO_INIT_TYPE flags)  
```  
  
#### <a name="parameters"></a>参数  
 `flags`  
 一个 RO_INIT_TYPE 枚举，它指定由 Windows 运行时提供的支持。  
  
## <a name="remarks"></a>备注  
 RoInitializeWrapper 类将调用 Windows::Foundation::Initialize (*标志*)。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [HandleT 类](../windows/handlet-class.md)