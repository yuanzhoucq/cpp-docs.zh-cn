---
title: 3.2 锁函数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0ec855c6-55a9-49d7-bee4-5edae6e86a1b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 97f125129d4b35586111f3d4092d457560aaebec
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412270"
---
# <a name="32-lock-functions"></a>3.2 锁函数

在本部分中所述的函数来操作用于同步的锁。

对于以下函数，锁定变量必须具有类型**omp_lock_t**。 此变量仅必须通过这些函数来访问。 所有锁函数都要求参数具有一个指向**omp_lock_t**类型。

- `omp_init_lock`函数初始化是简单的锁定。

- `omp_destroy_lock`函数删除是简单的锁定。

- `omp_set_lock`函数等待可用是简单的锁定之前。

- `omp_unset_lock`函数会释放是简单的锁定。

- `omp_test_lock`函数测试一个简单的锁。

对于以下函数，锁定变量必须具有类型**omp_nest_lock_t**。  此变量仅必须通过这些函数来访问。 所有可嵌套锁函数要求参数具有一个指向**omp_nest_lock_t**类型。

- `omp_init_nest_lock`函数初始化可嵌套锁。

- `omp_destroy_nest_lock`函数可删除可嵌套锁。

- `omp_set_nest_lock`函数等待直到可嵌套锁可用。

- `omp_unset_nest_lock`函数释放可嵌套锁。

- `omp_test_nest_lock`函数测试可嵌套锁。

OpenMP 的锁函数访问它们始终读取和更新锁定变量的最新值的方式中的锁定变量。 因此，不包括显式 OpenMP 程序所需**刷新**指令以确保锁定变量的值在不同线程之间保持一致。 (可能需要**刷新**指令以使其他变量的值保持一致。)