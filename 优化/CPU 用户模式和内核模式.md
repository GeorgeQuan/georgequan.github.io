CPU在现代计算机操作系统中被划分为用户空间（User Space）和内核空间（Kernel Space）。这两个空间的主要区别在于它们的权限级别和运行的内容。

- **用户空间**：这是应用程序和一些驱动程序执行的内存区域。用户空间的应用程序不能直接访问系统的硬件资源，它们必须通过系统调用向内核请求这些资源。用户空间提供了一种沙盒环境，限制了用户进程访问操作系统内核的能力。用户空间的进程只能访问有限的内存部分，并且只能通过系统调用间接访问内核空间[2](https://www.educative.io/answers/what-is-the-difference-between-the-kernel-and-user-spaces)[3](https://unix.stackexchange.com/questions/87625/what-is-difference-between-user-space-and-kernel-space)[5](https://medium.com/@shahneel2409/userspace-vs-kernel-space-a-comprehensive-guide-8f9b96cd6426)。

- **内核空间**：这是操作系统核心（内核）、内核扩展和大多数设备驱动程序运行的内存空间。内核空间严格保留用于运行操作系统内核、内核扩展和大多数设备驱动程序。内核空间具有对所有内存和机器硬件的完全访问权限，这对于内核执行其基本任务，如调度进程、管理内存和处理中断至关重要[2](https://www.educative.io/answers/what-is-the-difference-between-the-kernel-and-user-spaces)[3](https://unix.stackexchange.com/questions/87625/what-is-difference-between-user-space-and-kernel-space)[5](https://medium.com/@shahneel2409/userspace-vs-kernel-space-a-comprehensive-guide-8f9b96cd6426)。

这两种空间的分离是操作系统设计中的一个基本原则，它为安全性、稳定性和性能提供了多项好处：

- **安全性**：它防止用户空间应用程序无意或恶意地破坏内核或其他系统资源。
- **稳定性**：它使操作系统更加稳定，通过隔离内核与用户空间应用程序的潜在故障。
- **性能**：它可以通过允许内核在受保护的环境中运行来提高操作系统的性能[5](https://medium.com/@shahneel2409/userspace-vs-kernel-space-a-comprehensive-guide-8f9b96cd6426)。

例如，当你运行一个简单的Linux `ls`命令时，`ls`命令会通过系统调用向内核请求列出当前目录中的文件。内核接收到系统调用后执行请求的操作，并将结果返回给`ls`命令。这个过程展示了用户空间应用程序如何通过系统调用与内核交互，以及内核空间的重要性[5](https://medium.com/@shahneel2409/userspace-vs-kernel-space-a-comprehensive-guide-8f9b96cd6426)。