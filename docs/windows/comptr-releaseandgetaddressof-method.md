---
title: 'Comptr:: Releaseandgetaddressof 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf
dev_langs:
- C++
helpviewer_keywords:
- ReleaseAndGetAddressOf method
ms.assetid: 3751dcb4-d50e-432c-89e4-e736be34d434
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9d55241ddefce0e4fcd7f72698779d6e4ec97e20
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464988"
---
# <a name="comptrreleaseandgetaddressof-method"></a>ComPtr::ReleaseAndGetAddressOf 方法
释放与此关联的接口**ComPtr** ，然后检索的地址[ptr_](../windows/comptr-ptr-data-member.md)数据成员，其中包含指向已释放接口的指针。  
  
## <a name="syntax"></a>语法  
  
```  
T** ReleaseAndGetAddressOf();  
```  
  
## <a name="return-value"></a>返回值  
 地址[ptr_](../windows/comptr-ptr-data-member.md)数据成员**ComPtr**。  
  
## <a name="requirements"></a>要求  
 **标头：** client.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [ComPtr 类](../windows/comptr-class.md)   
 [ComPtr::ptr_ 数据成员](../windows/comptr-ptr-data-member.md)