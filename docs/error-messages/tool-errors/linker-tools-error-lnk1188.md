---
title: 链接器工具错误 LNK1188
ms.date: 11/04/2016
f1_keywords:
- LNK1188
helpviewer_keywords:
- LNK1188
ms.assetid: 4af574b0-5b41-4580-9a37-52a634add995
ms.openlocfilehash: 69ac20522aebb7391319c0de210e06b305f3fd0d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461251"
---
# <a name="linker-tools-error-lnk1188"></a>链接器工具错误 LNK1188

BADFIXUPSECTION:: 无效的链接地址信息目标 symbol;可能为零长度部分

在 VxD 链接期间的重定位的目标没有一个部分。 使用 LINK386 （较旧版本），（由 MASM 组指令生成） 的 OMF 组记录可能已使用组合与另一个非零长度部分零长度的节。 COFF 格式不支持 GROUP 指令和长度为零的部分。 当链接会自动将此类型的 OMF 对象转换到 COFF 时，可能会发生此错误。