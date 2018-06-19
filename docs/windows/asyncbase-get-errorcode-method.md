---
title: 'Asyncbase:: Get_errorcode 方法 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::get_ErrorCode
dev_langs:
- C++
helpviewer_keywords:
- get_ErrorCode method
ms.assetid: 50b4f8a2-9a21-4ea0-bb5d-7ff524d62aea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 88d2dd1d09b573b89e69d28071c7f689fa8396d7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33859626"
---
# <a name="asyncbasegeterrorcode-method"></a>AsyncBase::get_ErrorCode 方法
检索当前的异步操作的错误代码。  
  
## <a name="syntax"></a>语法  
  
```  
STDMETHOD(  
   get_ErrorCode  
)(HRESULT* errorCode) override;  
```  
  
#### <a name="parameters"></a>参数  
 `errorCode`  
 存储的当前错误代码的位置。  
  
## <a name="return-value"></a>返回值  
 如果成功，则则为 S_OK否则为如果关闭当前的异步操作的 E_ILLEGAL_METHOD_CALL。  
  
## <a name="requirements"></a>要求  
 **标头：** async.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [AsyncBase 类](../windows/asyncbase-class.md)