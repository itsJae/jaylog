---
title: "[CS Fundamentals] Thread Synchronization: Semaphore, Mutex, and Lock"
seoTitle: "[CS Fundamentals] Thread Synchronization: Semaphore, Mutex, and Lock"
seoDescription: "Semaphore

In a multi-threaded environment, your program might run into a problem if more than one threads are trying to acquire a shared resource at the sa"
datePublished: Thu Jan 23 2025 14:04:48 GMT+0000 (Coordinated Universal Time)
cuid: cm69en0pq001e09i3bltf6itj
slug: thread-synchronization
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1737639808868/680cba93-5fe1-4057-a207-d90c3c76f3e7.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1737641074438/ff5bdaf5-3431-4674-b5e5-798795024a8a.png
tags: computer-science, threads, threading, semaphore, lock, mutex, cs-fundamentals

---

---

## Semaphore vs Mutex

### Semaphore

In a multi-threaded environment, your program might run into a problem if more than one threads are trying to acquire a shared resource at the same time. **Semaphore** is a synchronization tool used in programming to manage access to a shared resource.

In real-life, you should wait for a person in the toilet because a toilet’s max capacity is one person at a time. There can’t be two people using a toilet. Semaphore uses that idea, restricting a process to wait until the current process ends using the shared resource.

Take not that semaphore can have multiple locks, which means it can have four toilets while mutex has only one.

### Mutex **(**short for Mutual Exclusion**)**

Mutex is a synchronization mechanism used in programming to control access to a shared resource in a multi-threaded environment. When a thread wants to access a shared resource, it must first “**lock**” the mutex. If another thread wants to use the resource, it must wait until it “**unlocks**”.

Take note that the mutex can give only one lock to a process.

### Similarities

Both are to prevent race conditions.

### Difference

> Sempahore can be a mutex, but the mutex can’t be the semaphore.

* **Mutex** = One lock, one thread can hold it at a time.
    
* **Semaphore** = Can have multiple locks (based on its counter value), so multiple threads can access the resource simultaneously, up to the limit set by the counter.
    

---

## Example with Code

Let’s have a look at this code:

```python
import logging
from concurrent.futures import ThreadPoolExecutor
import time

class FakeDataStore:
    def __init__(self):
        self.value = 0

    def update(self, n):
        logging.info("Thread %s: starting update", n)

        local_copy = self.value
        local_copy += 1
        time.sleep(0.1)
        self.value = local_copy

        logging.info("Thread %s: finishing update", n)

if __name__ == '__main__':
    format = "%(asctime)s: %(message)s"
    logging.basicConfig(format=format, level=logging.INFO, datefmt="%H:%M:%S")
    logging.info('Main-Thread: before creating and running thread.')
    store = FakeDataStore()
    logging.info("Testing update. Starting value is %d", store.value)

    with ThreadPoolExecutor(max_workers=2) as executor:
        for n in ['First', 'Second', 'Third']:
            executor.submit(store.update, n)

    logging.info("Testing update. Ending value is %d", store.value)
```

Output:

```plaintext
13:59:45: Main-Thread: before creating and running thread.
13:59:45: Testing update. Starting value is 0
13:59:45: Thread First: starting update
13:59:45: Thread Second: starting update
13:59:45: Thread First: finishing update
13:59:45: Thread Third: starting update
13:59:45: Thread Second: finishing update
13:59:45: Thread Third: finishing update
13:59:45: Testing update. Ending value is 2
```

The problem is that the ending value is 2. As we have executed three threads, it must be 3. The reason that this problem occurs is that we did not synchronize our threads.

We can perform a thread synchronization by using `threading.Lock()` of threading module.

Solution (adding lock):

```python
import logging
from concurrent.futures import ThreadPoolExecutor
import time
import threading

class FakeDataStore:
    def __init__(self):
        self.value = 0
        # create lock
        self._lock = threading.Lock()

    def update(self, n):
        logging.info("Thread %s: starting update", n)

        with self._lock:
            logging.info('Thread %s has lock', n)

            local_copy = self.value
            local_copy += 1
            time.sleep(0.1)
            self.value = local_copy

            logging.info("Thread %s: finishing update", n)

if __name__ == '__main__':
    format = "%(asctime)s: %(message)s"
    logging.basicConfig(format=format, level=logging.INFO, datefmt="%H:%M:%S")
    logging.info('Main-Thread: before creating and running thread.')
    store = FakeDataStore()
    logging.info("Testing update. Starting value is %d", store.value)

    with ThreadPoolExecutor(max_workers=2) as executor:
        for n in ['First', 'Second', 'Third']:
            executor.submit(store.update, n)

    logging.info("Testing update. Ending value is %d", store.value)
```

Output:

```plaintext
14:01:13: Main-Thread: before creating and running thread.
14:01:13: Testing update. Starting value is 0
14:01:13: Thread First: starting update
14:01:13: Thread First has lock
14:01:13: Thread Second: starting update
14:01:13: Thread First: finishing update
14:01:13: Thread Third: starting update
14:01:13: Thread Third has lock
14:01:13: Thread Third: finishing update
14:01:13: Thread Second has lock
14:01:13: Thread Second: finishing update
14:01:13: Testing update. Ending value is 3
```