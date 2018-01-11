---
title: "__svm_clgi |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __svm_clgi
dev_langs: C++
helpviewer_keywords:
- CLGI instruction
- __svm_clgi intrinsic
ms.assetid: 6640f5ab-9472-46f9-a042-e15c4f1ff858
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3fe7aacf6a337235e40c9d681ddce1928fe28c2e
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2018
---
# <a name="svmclgi"></a>__svm_clgi
**Microsoft 专用**  
  
 清除全局中断标志。  
  
## <a name="syntax"></a>语法  
  
```  
void __svm_clgi( void );  
```  
  
## <a name="remarks"></a>备注  
 `__svm_clgi`函数等同于`CLGI`计算机指令。 全局中断标志确定微处理器忽略、 推迟，或处理中断遇到 I/O 完成时，硬件温度警报或调试异常等事件。  
  
 此函数支持主机的虚拟机监视器与来宾操作系统及其应用程序进行交互。 有关详细信息，搜索文档中，"AMD64 体系结构程序员手动卷 2： 系统编程中，"在文档数 24593，修订 3.11， [AMD corporation](http://go.microsoft.com/fwlink/p/?linkid=23746)站点。  
  
## <a name="requirements"></a>惠?  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`__svm_clgi`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **标头文件** \<intrin.h >  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [__svm_stgi](../intrinsics/svm-stgi.md)