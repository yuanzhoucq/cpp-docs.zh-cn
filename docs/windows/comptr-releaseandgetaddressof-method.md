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
ms.openlocfilehash: e3efdce7cde39431a8d6f097aace2ed2f5a66b4d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589942"
---
# <a name="comptrreleaseandgetaddressof-method"></a>ComPtr::ReleaseAndGetAddressOf 方法

释放与此关联的接口**ComPtr** ，然后检索的地址[ptr_](../windows/comptr-ptr-data-member.md)数据成员，其中包含指向已释放接口的指针。

## <a name="syntax"></a>语法

```cpp
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