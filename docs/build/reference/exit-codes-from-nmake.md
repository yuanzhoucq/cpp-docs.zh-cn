---
title: 从 NMAKE 退出代码
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, exit codes
- exit codes
ms.assetid: 75f6913c-1da5-4572-a2d3-8a4e058bed15
ms.openlocfilehash: 25ea4060e7b7a968b6a9da78f344e645c5d43a44
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57824471"
---
# <a name="exit-codes-from-nmake"></a>从 NMAKE 退出代码

NMAKE 返回以下退出代码：

|代码|含义|
|----------|-------------|
|0|无错误 （可能是警告）|
|1|不完整的生成 （仅在使用 /K 时发出）|
|2|程序错误，可能是由于以下值之一：|
||的在生成文件中语法错误|
||的从命令错误或退出代码|
||-由用户中断|
|4|系统错误-内存不足|
|255|目标不是最新的 （仅在使用 /Q 时发出）|

## <a name="see-also"></a>请参阅

[运行 NMAKE](running-nmake.md)
