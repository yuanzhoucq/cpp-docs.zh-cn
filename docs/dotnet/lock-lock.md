---
title: lock::lock |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- lock::lock
- lock.lock
- msclr.lock.lock
- msclr::lock::lock
dev_langs:
- C++
helpviewer_keywords:
- lock constructor
ms.assetid: c9ad6c71-36ec-49c5-8ebd-f5c3a0cc94f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 76991eb9910e046ecdb76f3f169f7d410b38288e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428728"
---
# <a name="locklock"></a>lock::lock

构造`lock`对象，可以选择等待下去，为指定的量的时间，或者根本不获取锁。

## <a name="syntax"></a>语法

```
template<class T> lock(
   T ^ _object
);
template<class T> lock(
   T ^ _object,
   int _timeout
);
template<class T> lock(
   T ^ _object,
   System::TimeSpan _timeout
);
template<class T> lock(
   T ^ _object,
   lock_later
);
```

#### <a name="parameters"></a>参数

*（_o)*<br/>
要锁定的对象。

*超时) (_t*<br/>
超时值以毫秒为单位或作为<xref:System.TimeSpan>。

## <a name="exceptions"></a>异常

引发<xref:System.ApplicationException>如果获取锁超时前不会发生。

## <a name="remarks"></a>备注

构造函数的前三个窗体上获取锁的尝试`_object`指定的超时期限内 (或<xref:System.Threading.Timeout.Infinite>如果未指定)。

第四个形式的构造函数不会在获取锁`_object`。 `lock_later` 是的成员[lock_when 枚举](../dotnet/lock-when-enum.md)。 使用[lock::acquire](../dotnet/lock-acquire.md)或[lock::try_acquire](../dotnet/lock-try-acquire.md)这种情况下获取的锁。

当调用的析构函数时，将自动释放锁。

`_object` 不能为 <xref:System.Threading.ReaderWriterLock>。  如果是，将导致编译器错误。

## <a name="example"></a>示例

此示例跨多个线程使用单个类的实例。  类自身上使用锁来确保对其内部数据的访问是为每个线程保持一致。  主应用程序线程的类的同一实例上使用锁来定期检查以查看任何工作线程仍存在，并等待，直到所有工作线程退出已完成其任务。

```
// msl_lock_lock.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

ref class CounterClass {
private:
   int Counter;

public:
   property int ThreadCount;

   // function called by multiple threads, use lock to keep Counter consistent
   // for each thread
   void UseCounter() {
      try {
         lock l(this); // wait infinitely

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         for (int i = 0; i < 10; i++) {
            Counter++;
            Thread::Sleep(10);
         }

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         Counter = 0;
         // lock is automatically released when it goes out of scope and its destructor is called
      }
      catch (...) {
         Console::WriteLine("Couldn't acquire lock!");
      }

      ThreadCount--;
   }
};

int main() {
   // create a few threads to contend for access to the shared data
   CounterClass^ cc = gcnew CounterClass;
   array<Thread^>^ tarr = gcnew array<Thread^>(5);
   ThreadStart^ startDelegate = gcnew ThreadStart(cc, &CounterClass::UseCounter);
   for (int i = 0; i < tarr->Length; i++) {
      tarr[i] = gcnew Thread(startDelegate);
      cc->ThreadCount++;
      tarr[i]->Start();
   }

   // keep our main thread alive until all worker threads have completed
   lock l(cc, lock_later); // don't lock now, just create the object
   while (true) {
      if (l.try_acquire(50)) { // try to acquire lock, don't throw an exception if can't
         if (0 == cc->ThreadCount) {
            Console::WriteLine("All threads completed.");
            break; // all threads are gone, exit while
         }
         else {
            Console::WriteLine("{0} threads exist, continue waiting...", cc->ThreadCount);
            l.release(); // some threads exist, let them do their work
         }
      }
   }
}
```

```Output
In thread 3, Counter = 0
In thread 3, Counter = 10
In thread 5, Counter = 0
In thread 5, Counter = 10
In thread 7, Counter = 0
In thread 7, Counter = 10
In thread 4, Counter = 0
In thread 4, Counter = 10
In thread 6, Counter = 0
In thread 6, Counter = 10
All threads completed.
```

## <a name="requirements"></a>要求

**标头文件** \<msclr\lock.h >

**Namespace** msclr

## <a name="see-also"></a>请参阅

[lock 成员](../dotnet/lock-members.md)<br/>
[lock::~lock](../dotnet/lock-tilde-lock.md)<br/>
[lock::acquire](../dotnet/lock-acquire.md)<br/>
[lock::try_acquire](../dotnet/lock-try-acquire.md)