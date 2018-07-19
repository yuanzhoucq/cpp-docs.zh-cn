---
title: CDynamicAccessor::SetBlobSizeLimit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicAccessor::SetBlobSizeLimit
- SetBlobSizeLimit
- CDynamicAccessor.SetBlobSizeLimit
- ATL.CDynamicAccessor.SetBlobSizeLimit
- ATL::CDynamicAccessor::SetBlobSizeLimit
dev_langs:
- C++
helpviewer_keywords:
- SetBlobSizeLimit method
ms.assetid: fb8cb85d-f841-408e-a344-37895b10993f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8731857507fa096d500a31f31a7c31ef4f94cfc6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096075"
---
# <a name="cdynamicaccessorsetblobsizelimit"></a>CDynamicAccessor::SetBlobSizeLimit
以字节为单位设置的最大 BLOB 大小。  
  
## <a name="syntax"></a>语法  
  
```cpp
      void SetBlobSizeLimit(DBLENGTH nBlobSize);  
```  
  
#### <a name="parameters"></a>参数  
 `nBlobSize`  
 指定的 BLOB 大小限制。  
  
## <a name="remarks"></a>备注  
 以字节为单位; 设置的最大 BLOB 大小大于此值的列数据将被视为 BLOB。 某些提供程序 （例如 2 GB) 的列提供了极大的大小。 而不是尝试此大小为列分配内存，你通常会尝试将这些列作为 Blob 绑定。 这样你无需分配所有内存，但你仍可以阅读而不必担心截断的所有数据。 但是，在某些情况的下，在其中你可能想要强制`CDynamicAccessor`若要将大型列中其本机数据类型的绑定。 若要执行此操作，调用`SetBlobSizeLimit`之前调用**打开**。  
  
 构造函数方法[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)设置为默认值为 8000 个字节的最大 BLOB 大小。  
  
## <a name="requirements"></a>要求  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDynamicAccessor 类](../../data/oledb/cdynamicaccessor-class.md)