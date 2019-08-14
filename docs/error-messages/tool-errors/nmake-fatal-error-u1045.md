---
title: NMAKE 错误 U1045
ms.date: 08/11/2019
f1_keywords:
- U1045
helpviewer_keywords:
- U1045
ms.assetid: dc70d162-14b9-4107-9237-7514044d72e3
ms.openlocfilehash: bdc28bcf02aea791a346a0a74915707fef551b8b
ms.sourcegitcommit: db1ed91fa7451ade91c3fb76bc7a2b857f8a5eef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/13/2019
ms.locfileid: "68980547"
---
# <a name="nmake-fatal-error-u1045"></a>NMAKE 错误 U1045

> 生成失败:*消息*

由于*消息*原因, NMAKE 调用的程序或命令失败。 当 NMAKE 调用另一个程序 (例如编译器或链接器) 时, 调用可能会失败。 或者, 被调用的程序可能会返回错误。 此消息用于报告错误。

若要解决此问题，请首先确定错误原因。 可以使用 NMAKE [/n](../../build/reference/running-nmake.md#nmake-options)选项报告的命令来验证环境设置, 并重复 NMAKE 在命令行上执行的操作。
