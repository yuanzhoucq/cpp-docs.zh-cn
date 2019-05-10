---
title: 预定义的规则
ms.date: 11/04/2016
helpviewer_keywords:
- rules, predefined
- NMAKE program, predefined rules
- predefined rules in NMAKE
ms.assetid: 638cdc3f-4aba-4b4f-96e3-ad65b0364f12
ms.openlocfilehash: 7a922a239306f10121791caa8f9f088cea88c019
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319442"
---
# <a name="predefined-rules"></a>预定义的规则

预定义的推理规则使用 NMAKE 提供命令和选项宏。

|规则|命令|默认<br /><br /> action|Batch<br /><br /> 规则|上运行的平台 nmake|
|----------|-------------|------------------------|--------------------|----------------------------|
|.asm.exe|$(AS) $(AFLAGS) $&LT;|ml $<|否|x86|
|.asm.obj|$(AS) $(AFLAGS) /c $<|ml /c $<|是|x86|
|.asm.exe|$(AS) $(AFLAGS) $&LT;|ml64 $<|否|X64|
|.asm.obj|$(AS) $(AFLAGS) /c $<|ml64 /c $<|是|X64|
|.c.exe|$(CC) $(CFLAGS) $&LT;|cl $<|否|全部|
|.c.obj|$(CC) $(CFLAGS) /c $<|cl /c $<|是|全部|
|.cc.exe|$(CC) $(CFLAGS) $&LT;|cl $<|否|全部|
|.cc.obj|$(CC) $(CFLAGS) /c $<|cl /c $<|是|全部|
|.cpp.exe|$(CPP) $(CPPFLAGS) $&LT;|cl $<|否|全部|
|.cpp.obj|$(CPP) $(CPPFLAGS) /c $<|cl /c $<|是|全部|
|.cxx.exe|$(CXX) $(CXXFLAGS) $&LT;|cl $<|否|全部|
|.cxx.obj|$(CXX) $(CXXFLAGS) /c $<|cl /c $<|是|全部|
|.rc.res|$(RC) $(RFLAGS) /r $<|rc /r $<|否|全部|

## <a name="see-also"></a>请参阅

[推理规则](inference-rules.md)
