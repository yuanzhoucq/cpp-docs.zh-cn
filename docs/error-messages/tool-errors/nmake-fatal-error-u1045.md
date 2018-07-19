---
title: NMAKE 错误 U1045 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1045
dev_langs:
- C++
helpviewer_keywords:
- U1045
ms.assetid: dc70d162-14b9-4107-9237-7514044d72e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 673b20dde7156025c6aa56c487433eebe9e77aa3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33316369"
---
# <a name="nmake-fatal-error-u1045"></a>NMAKE 错误 U1045
生成失败： 消息  
  
 由于给定原因，NMAKE 调用的程序或命令失败。 当 NMAKE 调用另一个程序（例如，编译器或链接器）时，调用可能会失败，或者可能由调用的程序返回一个错误。 此消息用于报告错误。  
  
 若要解决此问题，请首先确定错误原因。 你可以使用 NMAKE 报告的命令[/N](../../build/nmake-options.md)选项以验证环境设置，并重复命令行上 NMAKE 执行的操作。