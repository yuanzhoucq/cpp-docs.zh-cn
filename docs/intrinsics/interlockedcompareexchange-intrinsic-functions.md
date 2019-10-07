---
title: _InterlockedCompareExchange 内部函数
ms.date: 09/02/2019
f1_keywords:
- _InterlockedCompareExchange_HLERelease
- _InterlockedCompareExchange8_nf
- _InterlockedCompareExchange16_acq_cpp
- _InterlockedCompareExchange_acq_cpp
- _InterlockedCompareExchange16_rel_cpp
- _InterlockedCompareExchange64_rel_cpp
- _InterlockedCompareExchange_cpp
- _InterlockedCompareExchange16_cpp
- _InterlockedCompareExchange64_acq_cpp
- _InterlockedCompareExchange_acq
- _InterlockedCompareExchange64_rel
- _InterlockedCompareExchange64_nf
- _InterlockedCompareExchange_rel_cpp
- _InterlockedCompareExchange16_nf
- _InterlockedCompareExchange8
- _InterlockedCompareExchange64_np
- _InterlockedCompareExchange16_rel
- _InterlockedCompareExchange64_acq
- _InterlockedCompareExchange8_rel
- _InterlockedCompareExchange_HLEAcquire
- _InterlockedCompareExchange64_HLERelease
- _InterlockedCompareExchange64_cpp
- _InterlockedCompareExchange_np
- _InterlockedCompareExchange8_acq
- _InterlockedCompareExchange16_acq
- _InterlockedCompareExchange_rel
- _InterlockedCompareExchange64_HLEAcquire
- _InterlockedCompareExchange64
- _InterlockedCompareExchange16
- _InterlockedCompareExchange
helpviewer_keywords:
- _InterlockedCompareExchange16 intrinsic
- _InterlockedCompareExchange_acq intrinsic
- InterlockedCompareExchange_acq intrinsic
- _InterlockedCompareExchange intrinsic
- InterlockedCompareExchange64 intrinsic
- _InterlockedCompareExchange64_acq intrinsic
- InterlockedCompareExchange16 intrinsic
- _InterlockedCompareExchange_rel intrinsic
- InterlockedCompareExchange intrinsic
- InterlockedCompareExchange64_acq intrinsic
- InterlockedCompareExchange_rel intrinsic
- _InterlockedCompareExchange64 intrinsic
- InterlockedCompareExchange64_rel intrinsic
- _InterlockedCompareExchange64_rel intrinsic
ms.assetid: c3ad79c0-a523-4930-a3a4-69a65d7d5c81
ms.openlocfilehash: 26dff1c902fff495d5efe45d8da10b1c5da72878
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222052"
---
# <a name="_interlockedcompareexchange-intrinsic-functions"></a>_InterlockedCompareExchange 内部函数

**Microsoft 专用**

执行联锁比较和交换。

## <a name="syntax"></a>语法

```C
long _InterlockedCompareExchange(
   long volatile * Destination,
   long Exchange,
   long Comparand
);
long _InterlockedCompareExchange_acq(
   long volatile * Destination,
   long Exchange,
   long Comparand
);
long _InterlockedCompareExchange_HLEAcquire(
   long volatile * Destination,
   long Exchange,
   long Comparand
);
long _InterlockedCompareExchange_HLERelease(
   long volatile * Destination,
   long Exchange,
   long Comparand
);
long _InterlockedCompareExchange_np(
   long volatile * Destination,
   long Exchange,
   long Comparand
);
long _InterlockedCompareExchange_rel(
   long volatile * Destination,
   long Exchange,
   long Comparand
);
char _InterlockedCompareExchange8(
   char volatile * Destination,
   char Exchange,
   char Comparand
);
char _InterlockedCompareExchange8_acq(
   char volatile * Destination,
   char Exchange,
   char Comparand
);
char _InterlockedCompareExchange8_nf(
   char volatile * Destination,
   char Exchange,
   char Comparand
);
char _InterlockedCompareExchange8_rel(
   char volatile * Destination,
   char Exchange,
   char Comparand
);
short _InterlockedCompareExchange16(
   short volatile * Destination,
   short Exchange,
   short Comparand
);
short _InterlockedCompareExchange16_acq(
   short volatile * Destination,
   short Exchange,
   short Comparand
);
short _InterlockedCompareExchange16_nf(
   short volatile * Destination,
   short Exchange,
   short Comparand
);
short _InterlockedCompareExchange16_np(
   short volatile * Destination,
   short Exchange,
   short Comparand
);
short _InterlockedCompareExchange16_rel(
   short volatile * Destination,
   short Exchange,
   short Comparand
);
__int64 _InterlockedCompareExchange64(
   __int64 volatile * Destination,
   __int64 Exchange,
   __int64 Comparand
);
__int64 _InterlockedCompareExchange64_acq(
   __int64 volatile * Destination,
   __int64 Exchange,
   __int64 Comparand
);
__int64 _InterlockedCompareExchange64_HLEAcquire (
   __int64 volatile * Destination,
   __int64 Exchange,
   __int64 Comparand
);
__int64 _InterlockedCompareExchange64_HLERelease(
   __int64 volatile * Destination,
   __int64 Exchange,
   __int64 Comparand
);
__int64 _InterlockedCompareExchange64_nf(
   __int64 volatile * Destination,
   __int64 Exchange,
   __int64 Comparand
);
__int64 _InterlockedCompareExchange64_np(
   __int64 volatile * Destination,
   __int64 Exchange,
   __int64 Comparand
);
__int64 _InterlockedCompareExchange64_rel(
   __int64 volatile * Destination,
   __int64 Exchange,
   __int64 Comparand
);
```

### <a name="parameters"></a>参数

*位置*\
[in, out]指向目标值的指针。 忽略此标记。

*外汇*\
中交换值。 忽略此标记。

*比较字*\
中要与目标进行比较的值。 忽略此标记。

## <a name="return-value"></a>返回值

返回值是 `Destination` 指针的初始值。

## <a name="requirements"></a>要求

|内部函数|体系结构|Header|
|---------------|------------------|------------|
|`_InterlockedCompareExchange`, `_InterlockedCompareExchange8`, `_InterlockedCompareExchange16`, `_InterlockedCompareExchange64`|x86、ARM、x64、ARM64|\<intrin.h>|
|`_InterlockedCompareExchange_acq`, `_InterlockedCompareExchange_rel`, `_InterlockedCompareExchange8_acq`, `_InterlockedCompareExchange8_nf`, `_InterlockedCompareExchange8_rel`,`_InterlockedCompareExchange16_acq`, `_InterlockedCompareExchange16_nf`, `_InterlockedCompareExchange16_rel`, `_InterlockedCompareExchange64_acq`, `_InterlockedCompareExchange64_nf`, `_InterlockedCompareExchange64_rel`,|ARM, ARM64|\<intrin.h>|
|`_InterlockedCompareExchange_np`, `_InterlockedCompareExchange16_np`, `_InterlockedCompareExchange64_np`|X64|\<intrin.h>|
|`_InterlockedCompareExchange_HLEAcquire`, `_InterlockedCompareExchange_HLERelease`, `_InterlockedCompareExchange64_HLEAcquire`, `_InterlockedCompareExchange64_HLERelease`|x86、x64|\<immintrin.h>|

## <a name="remarks"></a>备注

`_InterlockedCompareExchange`执行`Destination` 值`Comparand`与值的原子比较。 如果 `Destination` 值等于 `Comparand` 值，`Exchange` 值将存储在由 `Destination` 指定的地址。 否则, 不执行任何操作。

`_InterlockedCompareExchange`为 Win32 Windows SDK [InterlockedCompareExchange](/windows/win32/api/winnt/nf-winnt-interlockedcompareexchange)函数提供编译器内部函数支持。

根据所涉及的数据`_InterlockedCompareExchange`类型以及是否使用特定于处理器的获取或发布语义, 中有几种不同的变化形式。

当函数对长整数值进行操作时`_InterlockedCompareExchange8` , 对8位整数值进行操作`_InterlockedCompareExchange16` , 对短整数值进行操作`_InterlockedCompareExchange64` , 并对64位整数值进行运算。 `_InterlockedCompareExchange`

在 ARM 平台上，可以使用带 `_acq` 和 `_rel` 后缀的内部函数获取和发布语义，例如在临界区的起始位置。 带`_nf` ("无围墙") 后缀的 ARM 内部函数不能充当内存屏障。

带 `_np`（“无预取”）后缀的函数可以阻止编译器插入可能的预取操作。

在支持硬件锁省略 (HLE) 指令的 Intel 平台，带 `_HLEAcquire` 和 `_HLERelease` 后缀的内部函数包括一个发送到处理器的提示，可以通过消除硬件中的锁写步骤来提升速度。 如果在不支持 HLE 的平台上调用这些内部函数, 则忽略该提示。

这些例程只能用作内部函数。

## <a name="example"></a>示例

在以下示例中，`_InterlockedCompareExchange` 用于简单的低等级线程同步。 此方法的限制是多线程编程的基础;其中介绍了互锁内部函数的典型用法。 要得到最佳结果，请使用 Windows API。 有关多线程编程的详细信息, 请参阅[编写多线程 Win32 程序](../parallel/multithreading-with-c-and-win32.md#writing-a-multithreaded-win32-program)。

```cpp
// intrinExample.cpp
// compile with: /EHsc /O2
// Simple example of using _Interlocked* intrinsics to
// do manual synchronization
//
// Add [-DSKIP_LOCKING] to the command line to disable
// the locking. This will cause the threads to execute out
// of sequence.

#define _CRT_RAND_S

#include "windows.h"

#include <iostream>
#include <queue>
#include <intrin.h>

using namespace std;

// --------------------------------------------------------------------

// if defined, will not do any locking on shared data
//#define SKIP_LOCKING

// A common way of locking using _InterlockedCompareExchange.
// Refer to other sources for a discussion of the many issues
// involved. For example, this particular locking scheme performs well
// when lock contention is low, as the while loop overhead is small and
// locks are acquired very quickly, but degrades as many callers want
// the lock and most threads are doing a lot of interlocked spinning.
// There are also no guarantees that a caller will ever acquire the
// lock.
namespace MyInterlockedIntrinsicLock
{
    typedef unsigned LOCK, *PLOCK;

#pragma intrinsic(_InterlockedCompareExchange, _InterlockedExchange)

    enum {LOCK_IS_FREE = 0, LOCK_IS_TAKEN = 1};

    void Lock(PLOCK pl)
    {
#if !defined(SKIP_LOCKING)
        // If *pl == LOCK_IS_FREE, it is set to LOCK_IS_TAKEN
        // atomically, so only 1 caller gets the lock.
        // If *pl == LOCK_IS_TAKEN,
        // the result is LOCK_IS_TAKEN, and the while loop keeps spinning.
        while (_InterlockedCompareExchange((long *)pl,
                                           LOCK_IS_TAKEN, // exchange
                                           LOCK_IS_FREE)  // comparand
               == LOCK_IS_TAKEN)
        {
            // spin!
        }
        // This will also work.
        //while (_InterlockedExchange(pl, LOCK_IS_TAKEN) ==
        //                             LOCK_IS_TAKEN)
        //{
        //    // spin!
        //}

        // At this point, the lock is acquired.
#endif
    }

    void Unlock(PLOCK pl) {
#if !defined(SKIP_LOCKING)
        _InterlockedExchange((long *)pl, LOCK_IS_FREE);
#endif
    }
}

// ------------------------------------------------------------------
// Data shared by threads

queue<int> SharedQueue;
MyInterlockedIntrinsicLock::LOCK SharedLock;
int TicketNumber;

// ------------------------------------------------------------------

DWORD WINAPI
ProducerThread(
    LPVOID unused
    )
{
    unsigned int randValue;
    while (1) {
        // Acquire shared data. Enter critical section.
        MyInterlockedIntrinsicLock::Lock(&SharedLock);

        //cout << ">" << TicketNumber << endl;
        SharedQueue.push(TicketNumber++);

        // Release shared data. Leave critical section.
        MyInterlockedIntrinsicLock::Unlock(&SharedLock);

        rand_s(&randValue);
        Sleep(randValue % 20);
    }

    return 0;
}

DWORD WINAPI
ConsumerThread(
    LPVOID unused
    )
{
    while (1) {
        // Acquire shared data. Enter critical section
        MyInterlockedIntrinsicLock::Lock(&SharedLock);

        if (!SharedQueue.empty()) {
            int x = SharedQueue.front();
            cout << "<" << x << endl;
            SharedQueue.pop();
        }

        // Release shared data. Leave critical section
        MyInterlockedIntrinsicLock::Unlock(&SharedLock);

        unsigned int randValue;
        rand_s(&randValue);
        Sleep(randValue % 20);
    }
    return 0;
}

int main(
    void
    )
{
    const int timeoutTime = 500;
    int unused1, unused2;
    HANDLE threads[4];

    // The program creates 4 threads:
    // two producer threads adding to the queue
    // and two consumers taking data out and printing it.
    threads[0] = CreateThread(NULL,
                              0,
                              ProducerThread,
                              &unused1,
                              0,
                              (LPDWORD)&unused2);

    threads[1] = CreateThread(NULL,
                              0,
                              ConsumerThread,
                              &unused1,
                              0,
                              (LPDWORD)&unused2);

    threads[2] = CreateThread(NULL,
                              0,
                              ProducerThread,
                              &unused1,
                              0,
                              (LPDWORD)&unused2);

    threads[3] = CreateThread(NULL,
                              0,
                              ConsumerThread,
                              &unused1,
                              0,
                              (LPDWORD)&unused2);

    WaitForMultipleObjects(4, threads, TRUE, timeoutTime);

    return 0;
}
```

```Output
<0
<1
<2
<3
<4
<5
<6
<7
<8
<9
<10
<11
<12
<13
<14
<15
<16
<17
<18
<19
<20
<21
<22
<23
<24
<25
<26
<27
<28
<29
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[_InterlockedCompareExchange128](../intrinsics/interlockedcompareexchange128.md)\
[_InterlockedCompareExchangePointer 内部函数](../intrinsics/interlockedcompareexchangepointer-intrinsic-functions.md)\
[编译器内部函数](../intrinsics/compiler-intrinsics.md)\
[关键字](../cpp/keywords-cpp.md)\
[与 x86 编译器冲突](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
