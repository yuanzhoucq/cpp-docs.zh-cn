---
title: "__incgsbyte、 __incgsword、 __incgsdword、 __incgsqword |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __incgsdword
- __incgsqword_cpp
- __incgsword_cpp
- __incgsword
- __incgsbyte
- __incgsbyte_cpp
- __incgsqword
- __incgsdword_cpp
dev_langs: C++
helpviewer_keywords:
- __incgsbyte intrinsic
- __incgsword intrinsic
- __incgsqword intrinsic
- __incgsdword intrinsic
ms.assetid: 06bfdf4f-7643-4fe0-8455-60ce3068073e
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 042858ea1568705050c5e10399a24f7bc24edd8f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="incgsbyte-incgsword-incgsdword-incgsqword"></a>__incgsbyte, __incgsword, __incgsdword, __incgsqword
**Microsoft 专用**  
  
 指定相对于开始的偏移量的内存位置添加一个为值`GS`段。  
  
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
|`__incgsbyte`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__incgsword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__incgsdword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__incgsqword`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
## <a name="remarks"></a>备注  
 这些内部函数只有在内核模式下可用，例程都仅可用作内部函数。  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [__addgsbyte， \__addgsword， \__addgsdword， \__addgsqword](../intrinsics/addgsbyte-addgsword-addgsdword-addgsqword.md)   
 [__readgsbyte， \__readgsdword， \__readgsqword， \__readgsword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)   
 [__writegsbyte， \__writegsdword， \__writegsqword， \__writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)   
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)