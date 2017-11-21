---
title: "Handlet:: Close 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleT::Close
dev_langs: C++
helpviewer_keywords: Close method
ms.assetid: 1b9d597c-abcf-4028-a068-0344560009f6
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 94c246153e5c7e159ccbfe4196ab3692f4138047
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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
  
## <a name="see-also"></a>另请参阅  
 [HandleT 类](../windows/handlet-class.md)