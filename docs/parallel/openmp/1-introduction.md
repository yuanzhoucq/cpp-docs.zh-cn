---
title: 1. 简介 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c42e72bc-0e31-4b1c-b670-cd82673c0c5a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ce963d312d145e26567a5902f32e45735eb1d89
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438413"
---
# <a name="1-introduction"></a>1.介绍

本文档指定编译器指令，库函数，以及可用于 C 和 c + + 程序中指定共享内存的并行度的环境变量的集合。 本文档中所述的功能统称为*OpenMP C/c + + 应用程序接口 (API)*。 此规范的目的是提供的并行编程模型允许跨不同供应商的共享内存体系结构为可移植程序。 将由从众多供应商的编译器支持 OpenMP C/c + + API。 OpenMP，有关详细信息包括*OpenMP Fortran 应用程序编程接口*，可以在以下网站上找到：

[http://www.openmp.org](http://www.openmp.org)

指令中，库函数和本文档中定义的环境变量将允许用户创建和管理并行程序，同时允许可移植性。 指令扩展 C 和 c + + 顺序编程模型与单个程序多个数据 (SPMD) 构造中，工作共享构造和同步结构，并为共享和私有化的数据提供支持。 OpenMP C 和 c + + API 支持的编译器将包括对编译器进行激活，并允许所有 OpenMP 编译器指令的解释的命令行选项。