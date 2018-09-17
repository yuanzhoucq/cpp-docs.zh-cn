---
title: 预定义规则 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rules, predefined
- NMAKE program, predefined rules
- predefined rules in NMAKE
ms.assetid: 638cdc3f-4aba-4b4f-96e3-ad65b0364f12
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a34d3d0a601b2e160f988e0fed34a630612d839
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719246"
---
# <a name="predefined-rules"></a>预定义的规则

预定义的推理规则使用 NMAKE 提供命令和选项宏。

|规则|命令|默认<br /><br /> action|Batch<br /><br /> 规则|上运行的平台 nmake|
|----------|-------------|------------------------|--------------------|----------------------------|
|。 asm.exe|$(AS) $(AFLAGS) $<|ml $<|否|x86|
|。 asm.obj|$(AS) $(AFLAGS) /c $<|ml /c $<|是|x86|
|。 asm.exe|$(AS) $(AFLAGS) $<|ml64 $<|否|X64|
|。 asm.obj|$(AS) $(AFLAGS) /c $<|ml64 /c $<|是|X64|
|。 c.exe|$(CC) $(CFLAGS) $<|cl $<|no|全部|
|。 c.obj|$(CC) $(CFLAGS) /c $<|cl /c $<|是|全部|
|。 cc.exe|$(CC) $(CFLAGS) $<|cl $<|no|全部|
|。 cc.obj|$(CC) $(CFLAGS) /c $<|cl /c $<|是|全部|
|。 cpp.exe|$(CPP) $(CPPFLAGS) $<|cl $<|no|全部|
|。 cpp.obj|$(CPP) $(CPPFLAGS) /c $<|cl /c $<|是|全部|
|。 cxx.exe|$(CXX) $(CXXFLAGS) $<|cl $<|no|全部|
|。 cxx.obj|$(CXX) $(CXXFLAGS) /c $<|cl /c $<|是|全部|
|。 rc.res|$(RC) $(RFLAGS) /r $<|rc /r $<|否|全部|

## <a name="see-also"></a>请参阅

[推理规则](../build/inference-rules.md)