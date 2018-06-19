---
title: 'Handlet:: Close 方法 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: 1b9d597c-abcf-4028-a068-0344560009f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4f0c1e47420106651cfe0526d6d212e9819a72ff
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873246"
---
# <a name="handletclose-method"></a>HandleT::Close 方法
关闭当前的 HandleT 对象。  
  
## <a name="syntax"></a>语法  
  
```  
void Close();  
```  
  
## <a name="remarks"></a>备注  
 关闭基于当前 HandleT 的句柄，然后将 HandleT 设置为无效状态。  
  
 如果句柄关闭不正确，则调用线程中将引发异常。  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>请参阅  
 [HandleT 类](../windows/handlet-class.md)