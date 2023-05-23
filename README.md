# RingTupleQueue: High-performance zero-copy storage and retrieval of variable-sized tuples in C++

RingTupleQueue is a WIP niche open-source library designed to handle
variable-length tuples in memory without the need for serialization,
deserialization or memory fragmentation. The library allows the creation,
storage, and retrieval of these tuples in a streamlined, efficient manner,
using a ring buffer architecture. These tuples must contain a timestamp,
and all tuples with a timestamp that does not fit with the timeframe of
the ring are overwritten. If it is not possible to overwrite any events,
then an exception is sent, the user might then decide to create a bigger
ring and copy all the information from the current RingTupleQueue to
the next one.

## Key Features

- **High Performance**: Designed with performance in mind, RingTupleQueue operates efficiently to handle data streams that can be maintained in RAM.
- **Zero-Copy**: Direct access to data in memory, minimizing the overhead of copying, serialization, and deserialization.
- **Queue Mechanism**: Leveraging a ring buffer structure, RingTupleQueue allows FIFO (First In, First Out) data management, ideal for streaming data.
- **Variable-Length Tuples**: Capable of handling variable-length tuples with multiple fields of different types.

## Installation

## (Planned) Usage

Include the RingTupleQueue header in your C++ file:

```cpp
#include "ringtuplequeue.h"
```

Create an instance of the RingTupleQueue:

```cpp
RingTupleQueue::TupleQueue myTupleQueue;
```

Create and add a tuple to the queue:

```cpp
TupleType new_tuple_type = myTupleQueue.declare_tuple_type(arg_types_vector);

Tuple myTuple = myTupleQueue.add_tuple(tuple_type, args_vector);
```

Retrieve a tuple from the queue:

```cpp
auto retrievedTuple = myTupleQueue.get_tuple(tuple_position);
```

Note: The `create_tuple` function throws an exception if the buffer is
full. The user must handle this exception and decide whether to increase
the buffer size, free up space, or fail the operation.

## Current supported values

1. string
2. int64_t
3. double
4. bool

## Contributing

We welcome contributions from the community. Please refer to the
CONTRIBUTING.md file for more information.

## License

This project is licensed under the terms of the MIT license. For more
information, see the LICENSE file.
