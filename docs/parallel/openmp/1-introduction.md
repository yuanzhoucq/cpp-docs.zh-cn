---
title: "1. 简介 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: c42e72bc-0e31-4b1c-b670-cd82673c0c5a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f850e236ebfd056da93700df06ec830e5a573284
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="1-introduction"></a>1.介绍
本文档指定编译器指令、 库函数和用于 C 和 c + + 程序中指定共享内存并行的环境变量的集合。 本文档中所述的功能统称为*OpenMP C/c + + 应用程序接口 (API)*。 本规范的目标是可以进行并行编程提供模型允许程序可以跨来自不同供应商的共享内存体系结构移植。 OpenMP C/c + + API 将从众多供应商的编译器支持。 OpenMP，有关详细信息包括*OpenMP Fortran 应用程序编程接口*，可以找到在以下网站：  
  
 [http://www.openmp.org](http://www.openmp.org)  
  
 指令，库函数和本文档中定义的环境变量将允许用户创建和管理允许可移植性时的并行程序。 指令扩展 C 和 c + + 顺序编程模型使用的单个程序多个数据 (SPMD) 构造、 工作共享构造和同步构造，并为共享和 privatization 数据提供支持。 支持的 OpenMP C 和 c + + API 的编译器将包括到激活，并允许解释所有 OpenMP 编译器指令的编译器命令行选项。