---
title: 卸载延迟加载的 DLL
ms.date: 11/04/2016
helpviewer_keywords:
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 6463bc71-020e-4aff-a4ca-90360411c54e
ms.openlocfilehash: 1895bf12cb195ef7b4555d400badf112d377547b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211913"
---
# <a name="unloading-a-delay-loaded-dll"></a>卸载延迟加载的 DLL

默认提供的延迟加载帮助程序将检查延迟加载描述符是否在 pUnloadIAT 字段中有一个指针和原始导入地址表（IAT）的副本。 如果是这样，则会将列表中的指针保存到导入延迟描述符。 这使 helper 函数能够按名称查找 DLL 以支持显式卸载该 DLL。

下面是用于显式卸载延迟加载的 DLL 的关联结构和函数：

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

UnloadInfo 结构是使用 c + + 类实现的，该 c + + 类将**LocalAlloc**和**LocalFree**实现分别用作运算符 **`new`** 和运算符 **`delete`** 。 这些选项保留在标准链接列表中，使用 __puiHead 作为列表的开头。

调用 __FUnloadDelayLoadedDLL 将尝试在加载的 Dll 列表中查找您提供的名称（需要完全匹配）。 如果找到，pUnloadIAT 中 IAT 的副本将复制到正在运行的 IAT 的顶部，以还原 thunk 指针，库将与**FreeLibrary**一起释放，匹配的**UnloadInfo**记录将从列表取消链接并被删除，并且返回 TRUE。

函数 __FUnloadDelayLoadedDLL2 的参数区分大小写。 例如，你可以指定：

```cpp
__FUnloadDelayLoadedDLL2("user32.DLL");
```

而不是：

```cpp
__FUnloadDelayLoadedDLL2("User32.DLL");.
```

## <a name="see-also"></a>另请参阅

[了解 Helper 函数](understanding-the-helper-function.md)
