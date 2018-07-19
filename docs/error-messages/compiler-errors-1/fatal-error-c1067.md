---
title: 错误 C1067 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1067
dev_langs:
- C++
helpviewer_keywords:
- C1067
ms.assetid: e2c94be6-4573-4571-aac9-73d657fe9f96
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 89ac7084e92f7f2ed496a4c1572e94a4fa46862f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229087"
---
# <a name="fatal-error-c1067"></a>错误 C1067
编译器限制： 已超出类型记录的大小的 64k 限制  
  
 如果符号的修饰的名超过 247 个字符，则可能发生此错误。  若要解决，缩短符号名称。  
  
 当编译器生成调试信息时，它会发出类型记录，以定义在源代码中遇到的类型。  例如，类型记录包括简单的结构和函数的自变量列表。  这些类型记录的一些可能是大型列表。  
  
 任何类型记录的大小上没有 64k 的限制。  如果超出该 64k 限制将发生此错误。  
  
 如果没有具有较长名称的多个符号，或者某个类、 结构或联合具有成员太多，也可能发生 C1067。