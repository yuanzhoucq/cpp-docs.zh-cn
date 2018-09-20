---
title: 3. 运行时库函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5c1a05df3b47c2bbf345bc0101f30ffb83b84967
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401837"
---
# <a name="3-run-time-library-functions"></a>3.运行时库函数

本部分介绍 OpenMP C 和 c + + 运行时库函数。 标头 **\<omp.h >** 声明两种类型，可用于控制和查询并行执行环境，并锁定可用于同步对数据的访问的函数的几个函数。

类型**omp_lock_t**是一种对象类型能够表示锁定就可用，或一个线程拥有的锁。 这些锁嘿*简单锁*。

类型**omp_nest_lock_t**是一种对象类型能够表示任一的锁定就是可用，或这两个线程的标识拥有锁和一个*嵌套计数*（如下所述）。 这些锁嘿*可嵌套锁*。

库函数是使用"C"链接的外部函数。

本章说明分为以下主题：

- 执行环境函数 (请参阅[第 3.1 节](../../parallel/openmp/3-1-execution-environment-functions.md)第 35 页上)。

- 锁定函数 (请参阅[第 3.2 节](../../parallel/openmp/3-2-lock-functions.md)第 41 页上)。