---
title: marshal_context 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- marshal_context
dev_langs:
- C++
helpviewer_keywords:
- marshal_context class [C++]
ms.assetid: 241b0cf6-4ca4-4812-aaee-d671c11dc034
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6bf712e960cbf96ccef6c3a3e4efebdad9045818
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="marshalcontext-class"></a>marshal_context 类
此类将在本机和托管环境之间转换数据。  
  
## <a name="syntax"></a>语法  
  
```  
class marshal_context  
```  
  
## <a name="remarks"></a>备注  
 对于需要上下文的数据转换，请使用 `marshal_context` 类。 请参阅[概述的封送处理在 c + +](../dotnet/overview-of-marshaling-in-cpp.md)有关的转换需要上下文和哪些封送处理文件必须是包含详细信息。 使用上下文时的封送处理结果直到销毁 `marshal_context` 对象才有效。 若要保留结果，您必须复制数据。  
  
 同一个 `marshal_context` 可用于多个数据转换。 通过这种方式重用上下文将不影响之前封送处理调用的结果。  
  
## <a name="requirements"></a>要求  
 **标头文件：** \<msclr\marshal.h >， \<msclr\marshal_windows.h >， \<msclr\marshal_cppstd.h >，或\<msclr\marshal_atl.h >  
  
 **Namespace:** msclr::interop  
  
## <a name="see-also"></a>请参阅  
 [C + + 中的封送处理概述](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal_as](../dotnet/marshal-as.md)