---
title: -范围 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /RANGE
dev_langs:
- C++
helpviewer_keywords:
- /RANGE dumpbin option
- -RANGE dumpbin option
ms.assetid: 7eeba266-32be-49cc-a350-96bdf541f98a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d06d699500ba3ea441af61a2e2a5a0da3f96903a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374419"
---
# <a name="range"></a>/RANGE
修改 dumpbin 与其他 dumpbin 选项，如 /RAWDATA 或 /DISASM 一起使用时的输出。  
  
## <a name="syntax"></a>语法  
  
```  
/RANGE:vaMin[,vaMax]  
```  
  
## <a name="flags"></a>Flags  
 **vaMin**  
 您想要开始的 dumpbin 操作虚拟地址。  
  
 **vaMax** （可选）  
 您想要结束的 dumpbin 操作虚拟地址。 如果未指定，dumpbin 将转到文件末尾。  
  
## <a name="remarks"></a>备注  
 若要查看的映像的虚拟地址，用于映射文件映像 （RVA + 基本） **/DISASM**或 **/HEADERS** dumpbin 或在 Visual Studio 调试器中的反汇编窗口的选项。  
  
## <a name="example"></a>示例  
 在此示例中， **/范围**用于修改的显示 **/disasm**选项。 在此示例中，十进制数字的形式表示的起始值和结束值指定为十六进制数。  
  
```  
dumpbin /disasm /range:4219334,0x004061CD t.exe  
```  
  
## <a name="see-also"></a>请参阅  
 [DUMPBIN 选项](../../build/reference/dumpbin-options.md)