---
title: SEGMENT | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- SEGMENT
dev_langs:
- C++
helpviewer_keywords:
- SEGMENT directive
ms.assetid: e6f68367-6714-4f06-a79c-edfa88014430
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 253c3b389bd0411e6b5096e914b6a844c8f40805
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="segment"></a>SEGMENT
定义调用程序段*名称*具有段特性  
  
## <a name="syntax"></a>语法  
  
```  
  
   name SEGMENT [[READONLY]] [[align]] [[combine]] [[use]] [[characteristics]] ALIAS(string) [['class']]  
statements  
name ENDS  
```  
  
#### <a name="parameters"></a>参数  
 *align*  
 可以从中选择的段的起始地址的内存地址的范围。 对齐类型可以是以下之一：  
  
|对齐类型|起始地址|  
|----------------|----------------------|  
|**BYTE**|下一个可用的字节地址。|  
|**WORD**|下一个可用 word 地址 （每个单词的 2 字节）。|  
|**DWORD**|下一个可用的双字地址 （双字每 4 个字节）。|  
|**PARA**|下一个可用段落地址 （每个段落 16 个字节）。|  
|**PAGE**|下一个可用页面地址 （每页的 256 个字节）。|  
|**对齐**(*n*)|下一步可用 *n* th 字节地址。 有关详细信息，请参阅备注部分。|  
  
 如果未指定此参数， **PARA**默认情况下使用。  
  
 *combine*  
 **公共**，**堆栈**，**常见**，**内存**，**在 * * * 地址*，**私有**  
  
 *use*  
 **USE16**， **USE32**，**平面**  
  
 `characteristics`  
 **信息**，**读取**，**编写**，**执行**，**共享**， **NOPAGE**， **NOCACHE**，和**放弃**  
  
 这些 COFF 仅支持和对应于类似名称的 COFF 部分特征 (例如，**共享**对应于 IMAGE_SCN_MEM_SHARED)。 读取设置 IMAGE_SCN_MEM_READ 标志。 已过时的只读标志导致要清除 IMG_SCN_MEM_WRITE 标志的部分。 如果任何`characteristics`的设置，未使用的默认特征以及仅程序员指定标志生效。  
  
 `ALIAS(` `string` `)`  
 此字符串用作发出 COFF 对象中的节名称。  创建具有相同的外部名称，使用不同 MASM 段名称的多个部分。  
  
 不支持与**/omf**。  
  
 `class`  
 指定应如何组合以及装配文件中的排序段。 典型值为， `'DATA'`， `'CODE'`，`'CONST'`和 `'STACK'`  
  
## <a name="remarks"></a>备注  
 有关`ALIGN(n)`，`n`可能是介于 1 和 8192 的 2 的任何幂; 不支持**/omf**。  
  
## <a name="see-also"></a>请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)