# Veeam Test Task

## Task
You need to write a console program in C# to generate the signature of the specified file. The signature is generated as follows: the original file is divided into blocks of a given length (except for the last block), for each block the hash-function SHA256 is calculated, and together with its number is output to the console.

The program should be able to process files larger than the amount of RAM, and use the computational power of the multiprocessor system as efficiently as possible. Only standard classes and libraries from .NET (excluding ThreadPool, BackgroundWorker, TPL) may be used when working with threads.

Implementations using Threads are expected. The path to the input file and the block size are specified on the command line. If an error occurs during program execution, its text and StackTrace must be output to the console.

## Launch

### Visual Studio
If the program sees a debugger attached or finds no launch arguments, it will ask for the path to the file and the size of the block

### Command Line
Args:
  What | Why 
--- | --- 
**--input-path** *path* | Path to input file
**--block-size** *size* | Block size in bytes
**--output-path** *path* | *Not required* Path to output file. If not specified, the output is printed to the console
**--single-thread** | *Not required* If specified, the program will be executed in single-thread mode
**--hash-algorithm-name** *name* | *Not required* Name of the hashing algorithm, the default is SHA256

## Benchmark
|           Method | InputFilePath | BlockSize |        Mean |     Error |    StdDev | Gen 0 | Gen 1 | Gen 2 | Allocated |
|----------------- |-------------- |---------- |------------:|----------:|----------:|------:|------:|------:|----------:|
| SingleThreadImpl |   C:\32mb.bin |   4194304 |   120.83 ms |  0.911 ms |  0.852 ms |     - |     - |     - |      4 MB |
|  MultiThreadImpl |   C:\32mb.bin |   4194304 |    33.38 ms |  0.443 ms |  0.414 ms |     - |     - |     - |     24 MB |
| SingleThreadImpl |    C:\1gb.bin |   4194304 | 3,783.39 ms | 15.564 ms | 14.558 ms |     - |     - |     - |      4 MB |
|  MultiThreadImpl |    C:\1gb.bin |   4194304 |   684.39 ms |  3.102 ms |  2.749 ms |     - |     - |     - |     24 MB |
| SingleThreadImpl |    C:\1gb.bin | 134217728 | 3,811.87 ms | 12.248 ms | 11.457 ms |     - |     - |     - |    128 MB |
|  MultiThreadImpl |    C:\1gb.bin | 134217728 | 1,062.83 ms |  3.379 ms |  2.996 ms |     - |     - |     - |    768 MB |
