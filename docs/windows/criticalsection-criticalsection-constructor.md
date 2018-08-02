---
title: 'Criticalsection:: Criticalsection 构造函数 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::CriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CriticalSection, constructor
ms.assetid: 930b89be-4d74-46bd-8879-5dd4d15bcbd0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 866159a4b3cbacae8b7ad09154fb93707fe4baac
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467347"
---
# <a name="criticalsectioncriticalsection-constructor"></a>CriticalSection::CriticalSection 构造函数
初始化类似 mutex 对象、但只能由单一进程的线程使用的同步对象。  
  
## <a name="syntax"></a>语法  
  
```  
explicit CriticalSection(  
   ULONG spincount = 0  
);  
```  
  
#### <a name="parameters"></a>参数  
 *spincount*  
 关键部分对象的旋转计数。 默认值为 0。  
  
## <a name="remarks"></a>备注  
 有关关键部分和旋转计数的详细信息，请参阅`InitializeCriticalSectionAndSpinCount`函数，在**同步**部分 Windows API 文档。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [CriticalSection 类](../windows/criticalsection-class.md)