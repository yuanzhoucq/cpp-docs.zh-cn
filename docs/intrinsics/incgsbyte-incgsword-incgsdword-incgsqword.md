---
title: __incgsbyte，__incgsword，__incgsdword，__incgsqword |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __incgsdword
- __incgsqword_cpp
- __incgsword_cpp
- __incgsword
- __incgsbyte
- __incgsbyte_cpp
- __incgsqword
- __incgsdword_cpp
dev_langs:
- C++
helpviewer_keywords:
- __incgsbyte intrinsic
- __incgsword intrinsic
- __incgsqword intrinsic
- __incgsdword intrinsic
ms.assetid: 06bfdf4f-7643-4fe0-8455-60ce3068073e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 74e1b74c95f143aac7a915b3f148a85da9c5a3d3
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42543116"
---
# <a name="incgsbyte-incgsword-incgsdword-incgsqword"></a>__incgsbyte, __incgsword, __incgsdword, __incgsqword
**Microsoft 专用**  
  
 指定相对于开头的偏移量的内存位置中添加一个值`GS`段。  
  
## <a name="syntax"></a>语法  
  
```  
void __incgsbyte(   
   unsigned long Offset   
);  
void __incgsword(   
   unsigned long Offset   
);  
void __incgsdword(   
   unsigned long Offset  
);  
void __incgsqword(   
   unsigned long Offset   
);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `Offset`  
 从开始处的偏移量`GS`。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`__incgsbyte`|X64|  
|`__incgsword`|X64|  
|`__incgsdword`|X64|  
|`__incgsqword`|X64|  
  
## <a name="remarks"></a>备注  
 这些内部函数只有在内核模式下可用，例程都仅可用作内部函数。  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [__addgsbyte， \__addgsword， \__addgsdword， \__addgsqword](../intrinsics/addgsbyte-addgsword-addgsdword-addgsqword.md)   
 [__readgsbyte， \__readgsdword， \__readgsqword， \__readgsword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)   
 [__writegsbyte， \__writegsdword， \__writegsqword， \__writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)