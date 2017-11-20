---
title: "Asyncbase:: Close 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase::Close
dev_langs: C++
helpviewer_keywords: Close method
ms.assetid: a52b1124-754b-4393-b491-64aae0c22f1c
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: dbdc52eec476b973c3d3549cfb0ff9413a46f6f3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="asyncbaseclose-method"></a>AsyncBase::Close 方法
关闭的异步操作。  
  
## <a name="syntax"></a>语法  
  
```  
STDMETHOD(  
   Close  
)(void) override;  
```  
  
## <a name="return-value"></a>返回值  
 如果该操作将关闭，或者已经，则为 S_OK 关闭;否则为 E_ILLEGAL_STATE_CHANGE。  
  
## <a name="remarks"></a>备注  
 Close （） IAsyncInfo::Close，默认实现，并且不执行任何实际工作。 若要实际关闭异步操作，重写 OnClose() 纯虚方法。  
  
## <a name="requirements"></a>要求  
 **标头：** async.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>另请参阅  
 [AsyncBase 类](../windows/asyncbase-class.md)