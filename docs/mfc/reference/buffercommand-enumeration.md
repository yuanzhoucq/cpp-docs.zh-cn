---
title: BufferCommand 枚举
description: 描述 BufferCommand 枚举，该枚举用于通过 CMemFile：： GetBufferPtr （）处理内存文件
ms.date: 07/23/2020
f1_keywords:
- afx/buffercommand
helpviewer_keywords:
- buffercommand enumeration [MFC]
ms.openlocfilehash: f2f553df56fadd99b65b04cce9a97917425ed70b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212068"
---
# <a name="buffercommand-enumeration"></a>BufferCommand 枚举

由[CMemFile：： GetBufferPtr](cmemfile-class.md#getbufferptr)用于确定要对文件支持的内存缓冲区执行的操作。

## <a name="syntax"></a>语法

``` cpp
public enum BufferCommand
{
   bufferRead,
   bufferWrite,
   bufferCommit,
   bufferCheck
};
```

## <a name="members"></a>成员

|名称|描述|
|-|-|
| `bufferRead` | 读取文件支持的内存缓冲区。 |
| `bufferWrite` | 写入到文件支持的内存缓冲区。 |
| `bufferCommit` | 将文件支持的内存缓冲区中的当前位置前移到已提交缓冲区的末尾。 |
| `bufferCheck` | 确定文件支持的内存缓冲区的大小是否可以增长。 |

## <a name="requirements"></a>要求

**标头：** afxwinforms （在程序集 atlmfc\lib\mfcmifc80.dll 中定义）
