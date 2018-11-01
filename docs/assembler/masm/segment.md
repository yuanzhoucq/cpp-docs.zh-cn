---
title: SEGMENT
ms.date: 08/30/2018
f1_keywords:
- SEGMENT
helpviewer_keywords:
- SEGMENT directive
ms.assetid: e6f68367-6714-4f06-a79c-edfa88014430
ms.openlocfilehash: f37be47b92a71e20821cd1e40f8cf1350dfedaff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615418"
---
# <a name="segment"></a>SEGMENT

定义调用程序段*名称*具有段属性

## <a name="syntax"></a>语法

> *名称*段 [[只读]] [[*对齐*]] [[*合并*]] [[*使用*]] [[*特征*]] 别名 (*字符串*) [['*类*]]<br/>
> *语句*<br/>
> *名称*结束

#### <a name="parameters"></a>参数

*align*<br/>
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

*combine*<br/>
**公共**，**堆栈**，**常见**，**内存**，**在**<em>地址</em>， **专用**

*use*<br/>
**USE16**， **USE32**，**平面**

*特征*<br/>
**INFO**，**读取**，**编写**， **EXECUTE**，**共享**， **NOPAGE**， **NOCACHE**，和**放弃**

这些仅支持为 COFF，对应于类似名称的 COFF 节特征 (例如，**共享**对应于 IMAGE_SCN_MEM_SHARED)。 读取设置 IMAGE_SCN_MEM_READ 标志。 已过时的只读标志导致要清除 IMG_SCN_MEM_WRITE 标志的部分。 如果有的话*特征*进行设置，未使用的默认特性，并仅程序员指定标志是在起作用。

`ALIAS(` *字符串* `)`<br/>
此字符串用作发出 COFF 对象中的节名称。  创建多个部分具有相同的外部名称，使用不同的 MASM 段名称。

不支持使用 **/omf**。

*class*<br/>
指定应如何组合和组装文件中排序段。 典型值为， `'DATA'`， `'CODE'`，`'CONST'`和 `'STACK'`

## <a name="remarks"></a>备注

有关`ALIGN(n)`， *n*可以是任何电源 2 从 1 到 8192; 不支持 **/omf**。

## <a name="see-also"></a>请参阅

[指令参考](../../assembler/masm/directives-reference.md)<br/>