---
title: 卸载延迟加载的 DLL
ms.date: 11/04/2016
helpviewer_keywords:
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 6463bc71-020e-4aff-a4ca-90360411c54e
ms.openlocfilehash: 284a9cb9268c8c794379c6a5468b0f2b9092b7d0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317453"
---
# <a name="unloading-a-delay-loaded-dll"></a>卸载延迟加载的 DLL

默认提供的延迟加载 helper 进行检查以查看延迟加载描述符 pUnloadIAT 字段中是否具有一个指针，以及一份原始导入地址表 (IAT)。 如果是这样，它将保存到导入延迟描述符的列表中的指针。 这样，帮助程序函数可以按名称支持显式卸载该 DLL 中找到 DLL。

下面是关联的结构和函数的显式卸载延迟加载的 DLL:

```cpp
//
// Unload support from delayimp.h
//

// routine definition; takes a pointer to a name to unload

ExternC
BOOL WINAPI
__FUnloadDelayLoadedDLL2(LPCSTR szDll);

// structure definitions for the list of unload records
typedef struct UnloadInfo * PUnloadInfo;
typedef struct UnloadInfo {
    PUnloadInfo     puiNext;
    PCImgDelayDescr pidd;
    } UnloadInfo;

// from delayhlp.cpp
// the default delay load helper places the unloadinfo records in the
// list headed by the following pointer.
ExternC
PUnloadInfo __puiHead;
```

使用实现 UnloadInfo 结构C++类，该类使用**LocalAlloc**并**LocalFree**作为其运算符的实现**新**运算符和**删除**分别。 这些选项都保存在与列表的头使用 __puiHead 的标准链接列表。

调用 __FUnloadDelayLoadedDLL 将尝试查找名称 （完全匹配项是必需的） 加载 Dll 的列表中提供。 如果找到，将复制的副本中 pUnloadIAT IAT 上方的正在运行的 IAT，若要还原的转换 （thunk） 指针，库用来释放**FreeLibrary**，匹配**UnloadInfo**记录从已取消链接列表和删除，并且返回 TRUE。

函数 __FUnloadDelayLoadedDLL2 的参数是区分大小写。 例如，则会指定：

```cpp
__FUnloadDelayLoadedDLL2("user32.DLL");
```

而不是：

```cpp
__FUnloadDelayLoadedDLL2("User32.DLL");.
```

## <a name="see-also"></a>请参阅

[了解 Helper 函数](understanding-the-helper-function.md)
