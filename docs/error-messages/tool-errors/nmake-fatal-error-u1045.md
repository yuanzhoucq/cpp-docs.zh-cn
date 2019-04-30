---
title: NMAKE 错误 U1045
ms.date: 11/04/2016
f1_keywords:
- U1045
helpviewer_keywords:
- U1045
ms.assetid: dc70d162-14b9-4107-9237-7514044d72e3
ms.openlocfilehash: 0937e83303fefdf1f2aaaa5eea6f43c27159fd57
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344391"
---
# <a name="nmake-fatal-error-u1045"></a>NMAKE 错误 U1045

生成失败： 消息

由于给定原因，NMAKE 调用的程序或命令失败。 当 NMAKE 调用另一个程序（例如，编译器或链接器）时，调用可能会失败，或者可能由调用的程序返回一个错误。 此消息用于报告错误。

若要解决此问题，请首先确定错误原因。 您可以使用报告的 NMAKE 命令[/N](../../build/reference/nmake-options.md)选项来验证环境设置，并重复命令行上 NMAKE 执行的操作。