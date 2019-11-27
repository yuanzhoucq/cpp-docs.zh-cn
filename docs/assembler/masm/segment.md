---
title: SEGMENT
ms.date: 08/30/2018
f1_keywords:
- SEGMENT
helpviewer_keywords:
- SEGMENT directive
ms.assetid: e6f68367-6714-4f06-a79c-edfa88014430
ms.openlocfilehash: b7344d9cb685e0212748d7835e19f398f14979e7
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74393729"
---
# <a name="segment"></a>SEGMENT

定义名为*name*且带有段特性的程序段

## <a name="syntax"></a>语法

> *名称***段**⟦**READONLY**⟧⟦*align*⟧⟦*合并*⟧⟦*use*⟧⟦*特征*⟧ **ALIAS （** _string_ **）** ⟦ __"__ *class* __"__ ⟧ \
> *语句*\
> *名称***结束**

#### <a name="parameters"></a>参数

*align*<br/>
可以从中选择段的起始地址的内存地址范围。 对齐类型可以是以下任一项：

|对齐类型|起始地址|
|----------------|----------------------|
|**BYTE**|下一个可用的字节地址。|
|**WORD**|下一个可用的单词地址（每个单词2个字节）。|
|**DWORD**|下一个可用的双字地址（每个双引号4个字节）。|
|**分页**|下一个可用的段落地址（每段16个字节）。|
|**PAGE**|下一个可用页面地址（每页256字节）。|
|**ALIGN**（*n*）|下一个可用的第*n*个字节地址。 有关详细信息，请参阅备注部分。|

如果未指定此参数，则默认情况下使用**段落**。

*合并*\
**PUBLIC**、 **STACK**、 **COMMON**、 **MEMORY**、 **AT**<em>address</em>、 **PRIVATE**

*使用*\
**USE16**， **USE32**，**平面**

*特征*\
**INFO**、 **READ**、 **WRITE**、 **EXECUTE**、 **SHARED**、 **NOPAGE**、 **NOCACHE**和**放弃**

这些支持仅适用于 COFF，并对应于类似名称的 COFF 部分特征（例如， **SHARED**与 IMAGE_SCN_MEM_SHARED）相对应。 READ 设置 IMAGE_SCN_MEM_READ 标志。 过时的 READONLY 标志导致部分清除 IMG_SCN_MEM_WRITE 标志。 如果设置了任何*特征*，则不会使用默认特征，并且只有程序员指定的标志才有效。

_string_\
此字符串用作发出的 COFF 对象中的节名。  用不同的 MASM 段名称创建多个具有相同外部名称的节。

不支持 **/omf**。

*类*\
指定应如何在已组合的文件中组合和排序段。 典型值为、`'DATA'`、`'CODE'`、`'CONST'` 和 `'STACK'`

## <a name="remarks"></a>备注

对于 `ALIGN(n)`， *n*可以是从1到8192的2的任何幂;不支持 **/omf**。

## <a name="see-also"></a>另请参阅

[指令参考](directives-reference.md)
