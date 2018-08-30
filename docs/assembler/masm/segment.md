---
title: 段 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- SEGMENT
dev_langs:
- C++
helpviewer_keywords:
- SEGMENT directive
ms.assetid: e6f68367-6714-4f06-a79c-edfa88014430
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f5defce11b611f23b67e5e44ac1b9d406f73c0ae
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210414"
---
# <a name="segment"></a>SEGMENT
定义调用程序段*名称*具有段属性  
  
## <a name="syntax"></a>语法  
  
```  
  
   name SEGMENT [[READONLY]] [[align]] [[combine]] [[use]] [[characteristics]] ALIAS(string) [['class']]  
statements  
name ENDS  
```  
  
#### <a name="parameters"></a>参数  
 *align*  
 可以从中选择的段的起始地址的内存地址的范围。 对齐类型可以是下列之一：  
  
|对齐类型|开始地址|  
|----------------|----------------------|  
|**BYTE**|下一个可用的字节地址。|  
|**WORD**|下一个可用 word 地址 （每个单词的 2 个字节）。|  
|**DWORD**|下一个可用的双字地址 （每个双字 4 个字节）。|  
|**PARA**|下一个可用段落地址 （每个段落 16 个字节）。|  
|**PAGE**|下一个可用的页地址 （每页 256 个字节）。|  
|**对齐**(*n*)|下一个可用*n*个字节的地址。 有关详细信息，请参阅备注部分。|  
  
 如果未指定此参数， **PARA**默认情况下使用。  
  
 *combine*  
 **公共**，**堆栈**，**常见**，**内存**，**在**<em>地址</em>， **专用**  
  
 *use*  
 **USE16**， **USE32**，**平面**  
  
 `characteristics`  
 **INFO**，**读取**，**编写**， **EXECUTE**，**共享**， **NOPAGE**， **NOCACHE**，和**放弃**  
  
 这些仅支持为 COFF，对应于类似名称的 COFF 节特征 (例如，**共享**对应于 IMAGE_SCN_MEM_SHARED)。 读取设置 IMAGE_SCN_MEM_READ 标志。 已过时的只读标志导致要清除 IMG_SCN_MEM_WRITE 标志的部分。 如果任何`characteristics`进行设置，未使用的默认特性，并仅程序员指定标志是在起作用。  
  
 `ALIAS(` `string` `)`  
 此字符串用作发出 COFF 对象中的节名称。  创建多个部分具有相同的外部名称，使用不同的 MASM 段名称。  
  
 不支持使用 **/omf**。  
  
 `class`  
 指定应如何组合和组装文件中排序段。 典型值为， `'DATA'`， `'CODE'`，`'CONST'`和 `'STACK'`  
  
## <a name="remarks"></a>备注  
 有关`ALIGN(n)`，`n`可以是任何电源 2 从 1 到 8192; 不支持 **/omf**。  
  
## <a name="see-also"></a>请参阅  
 [指令参考](../../assembler/masm/directives-reference.md)