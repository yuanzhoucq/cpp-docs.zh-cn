---
title: 'RoInitializeWrapper:: ~ RoInitializeWrapper 析构函数 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::~RoInitializeWrapper
dev_langs:
- C++
ms.assetid: afef4c1f-ffde-4cd2-8654-8de4182eb5f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1c6eaeb044cf3e169bf5927a2fec948cc8d4294c
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606271"
---
# <a name="roinitializewrapperroinitializewrapper-destructor"></a>RoInitializeWrapper::~RoInitializeWrapper 析构函数
取消初始化 Windows 运行时。  
  
## <a name="syntax"></a>语法  
  
```cpp  
~RoInitializeWrapper()  
```  
  
## <a name="remarks"></a>备注  
 **RoInitializeWrapper**类调用`Windows::Foundation::Uninitialize()`。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [HandleT 类](../windows/handlet-class.md)