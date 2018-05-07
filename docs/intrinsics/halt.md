---
title: __halt |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __halt
- __halt_cpp
dev_langs:
- C++
helpviewer_keywords:
- __halt intrinsic
- HLT instruction
ms.assetid: a074f44a-101c-45a5-8a5e-cfd223c34002
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a36790eb1df098e6f663a30894c29a9ea14587b0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="halt"></a>__halt
**Microsoft 专用**  
  
 暂停微处理器，直到启用的中断、 不可屏蔽的中断 (NMI) 或重置的发生。  
  
## <a name="syntax"></a>语法  
  
```  
void __halt( void );  
```  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`__halt`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **标头文件** \<intrin.h >  
  
## <a name="remarks"></a>备注  
 `__halt`函数等同于`HLT`计算机指令，并仅在内核模式中可用。 有关详细信息，搜索文档中，"Intel 体系结构软件开发人员手册，卷 2： 指令集引用，"在[Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127)站点。  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)