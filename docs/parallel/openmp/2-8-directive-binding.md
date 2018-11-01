---
title: 2.8 指令绑定
ms.date: 11/04/2016
ms.assetid: 7bdac45e-ab55-42f0-bd47-a2e3d5bbab3e
ms.openlocfilehash: fb22d1b503303842ff73550c1c6544cae7e5f2f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528607"
---
# <a name="28-directive-binding"></a>2.8 指令绑定

动态指令的绑定必须遵守以下规则：

- **有关**，**部分**，**单一**，**主**，并**屏障**指令将绑定到动态封闭**并行**，如果存在，而不考虑任何值**如果**可能会显示该指令上的子句。 如果当前正在执行没有并行区域，由团队组成仅在主线程执行指令。

- **排序**指令将绑定到动态封闭**为**。

- **原子**指令强制执行独占访问与**原子**中所有线程，而不仅仅是当前团队的指令。

- **关键**指令强制执行独占访问与**关键**中所有线程，而不仅仅是当前团队的指令。

- 指令可以永远不会将绑定到最接近之外的任何指令动态封闭**并行**。