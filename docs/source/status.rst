.. Licensed to the Apache Software Foundation (ASF) under one
.. or more contributor license agreements.  See the NOTICE file
.. distributed with this work for additional information
.. regarding copyright ownership.  The ASF licenses this file
.. to you under the Apache License, Version 2.0 (the
.. "License"); you may not use this file except in compliance
.. with the License.  You may obtain a copy of the License at

..   http://www.apache.org/licenses/LICENSE-2.0

.. Unless required by applicable law or agreed to in writing,
.. software distributed under the License is distributed on an
.. "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
.. KIND, either express or implied.  See the License for the
.. specific language governing permissions and limitations
.. under the License.

=====================
Implementation Status
=====================

The following tables summarize the features available in the various official
Arrow libraries. All libraries currently follow version 1.0.0 of the Arrow
format. See :doc:`versioning` for details about versioning. Unless otherwise stated,
the Python, R, Ruby and C/GLib libraries follow the C++ Arrow library.

Data Types
==========

+-------------------+-------+-------+-------+------------+-------+-------+-------+
| Data type         | C++   | Java  | Go    | JavaScript | C#    | Rust  | Julia |
| (primitive)       |       |       |       |            |       |       |       |
+===================+=======+=======+=======+============+=======+=======+=======+
| Null              | ✓     | ✓     | ✓     |            |       |  ✓    | ✓     |
+-------------------+-------+-------+-------+------------+-------+-------+-------+
| Boolean           | ✓     | ✓     | ✓     | ✓          |  ✓    |  ✓    | ✓     |
+-------------------+-------+-------+-------+------------+-------+-------+-------+
| Int8/16/32/64     | ✓     | ✓     | ✓     | ✓          |  ✓    |  ✓    | ✓     |
+-------------------+-------+-------+-------+------------+-------+-------+-------+
| UInt8/16/32/64    | ✓     | ✓     | ✓     | ✓          |  ✓    |  ✓    | ✓     |
+-------------------+-------+-------+-------+------------+-------+-------+-------+
| Float16           |       |       | ✓     |            |       |       | ✓     |
+-------------------+-------+-------+-------+------------+-------+-------+-------+
| Float32/64        | ✓     | ✓     | ✓     | ✓          |  ✓    |  ✓    | ✓     |
+-------------------+-------+-------+-------+------------+-------+-------+-------+
| Decimal128        | ✓     | ✓     | ✓     |            |  ✓    |  ✓    | ✓     |
+-------------------+-------+-------+-------+------------+-------+-------+-------+
| Decimal256        | ✓     | ✓     |       |            |  ✓    |       | ✓     |
+-------------------+-------+-------+-------+------------+-------+-------+-------+
| Date32/64         | ✓     | ✓     | ✓     | ✓          |  ✓    |  ✓    | ✓     |
+-------------------+-------+-------+-------+------------+-------+-------+-------+
| Time32/64         | ✓     | ✓     | ✓     | ✓          |  ✓    |  ✓    | ✓     |
+-------------------+-------+-------+-------+------------+-------+-------+-------+
| Timestamp         | ✓     | ✓     | ✓     | ✓          |  ✓    |  ✓    | ✓     |
+-------------------+-------+-------+-------+------------+-------+-------+-------+
| Duration          | ✓     | ✓     | ✓     |            |       |  ✓    | ✓     |
+-------------------+-------+-------+-------+------------+-------+-------+-------+
| Interval          | ✓     | ✓     | ✓     |            |       |  ✓    | ✓     |
+-------------------+-------+-------+-------+------------+-------+-------+-------+
| Fixed Size Binary | ✓     | ✓     | ✓     | ✓          |  ✓    |  ✓    | ✓     |
+-------------------+-------+-------+-------+------------+-------+-------+-------+
| Binary            | ✓     | ✓     | ✓     | ✓          |  ✓    |  ✓    | ✓     |
+-------------------+-------+-------+-------+------------+-------+-------+-------+
| Large Binary      | ✓     | ✓     | ✓     | ✓          |       |  ✓    | ✓     |
+-------------------+-------+-------+-------+------------+-------+-------+-------+
| Utf8              | ✓     | ✓     | ✓     | ✓          |  ✓    |  ✓    | ✓     |
+-------------------+-------+-------+-------+------------+-------+-------+-------+
| Large Utf8        | ✓     | ✓     | ✓     | ✓          |       |  ✓    | ✓     |
+-------------------+-------+-------+-------+------------+-------+-------+-------+

+-------------------+-------+-------+-------+------------+-------+-------+-------+
| Data type         | C++   | Java  | Go    | JavaScript | C#    | Rust  | Julia |
| (nested)          |       |       |       |            |       |       |       |
+===================+=======+=======+=======+============+=======+=======+=======+
| Fixed Size List   | ✓     | ✓     | ✓     | ✓          |       |  ✓    | ✓     |
+-------------------+-------+-------+-------+------------+-------+-------+-------+
| List              | ✓     | ✓     | ✓     | ✓          |  ✓    |  ✓    | ✓     |
+-------------------+-------+-------+-------+------------+-------+-------+-------+
| Large List        | ✓     | ✓     |       |            |       |  ✓    | ✓     |
+-------------------+-------+-------+-------+------------+-------+-------+-------+
| Struct            | ✓     | ✓     | ✓     | ✓          |  ✓    |  ✓    | ✓     |
+-------------------+-------+-------+-------+------------+-------+-------+-------+
| Map               | ✓     | ✓     | ✓     | ✓          |       |       | ✓     |
+-------------------+-------+-------+-------+------------+-------+-------+-------+
| Dense Union       | ✓     | ✓     |       |            |       |       | ✓     |
+-------------------+-------+-------+-------+------------+-------+-------+-------+
| Sparse Union      | ✓     | ✓     |       |            |       |       | ✓     |
+-------------------+-------+-------+-------+------------+-------+-------+-------+

+-------------------+-------+-------+-------+------------+-------+-------+-------+
| Data type         | C++   | Java  | Go    | JavaScript | C#    | Rust  | Julia |
| (special)         |       |       |       |            |       |       |       |
+===================+=======+=======+=======+============+=======+=======+=======+
| Dictionary        | ✓     | ✓ (1) | ✓     | ✓ (1)      | ✓ (1) | ✓ (1) | ✓     |
+-------------------+-------+-------+-------+------------+-------+-------+-------+
| Extension         | ✓     | ✓     | ✓     |            |       |       | ✓     |
+-------------------+-------+-------+-------+------------+-------+-------+-------+

Notes:

* \(1) Nested dictionaries not supported

.. seealso::
   The :ref:`format_columnar` specification.


IPC Format
==========

+-----------------------------+-------+-------+-------+------------+-------+-------+-------+
| IPC Feature                 | C++   | Java  | Go    | JavaScript | C#    | Rust  | Julia |
|                             |       |       |       |            |       |       |       |
+=============================+=======+=======+=======+============+=======+=======+=======+
| Arrow stream format         | ✓     | ✓     | ✓     | ✓          |  ✓    |  ✓    | ✓     |
+-----------------------------+-------+-------+-------+------------+-------+-------+-------+
| Arrow file format           | ✓     | ✓     | ✓     | ✓          |  ✓    |  ✓    | ✓     |
+-----------------------------+-------+-------+-------+------------+-------+-------+-------+
| Record batches              | ✓     | ✓     | ✓     | ✓          |  ✓    |  ✓    | ✓     |
+-----------------------------+-------+-------+-------+------------+-------+-------+-------+
| Dictionaries                | ✓     | ✓     | ✓     | ✓          |  ✓    |  ✓    | ✓     |
+-----------------------------+-------+-------+-------+------------+-------+-------+-------+
| Replacement dictionaries    | ✓     | ✓     | ✓     |            |       |       | ✓     |
+-----------------------------+-------+-------+-------+------------+-------+-------+-------+
| Delta dictionaries          | ✓ (1) |       | ✓ (1) |            |  ✓    |       | ✓     |
+-----------------------------+-------+-------+-------+------------+-------+-------+-------+
| Tensors                     | ✓     |       |       |            |       |       |       |
+-----------------------------+-------+-------+-------+------------+-------+-------+-------+
| Sparse tensors              | ✓     |       |       |            |       |       |       |
+-----------------------------+-------+-------+-------+------------+-------+-------+-------+
| Buffer compression          | ✓     | ✓ (3) | ✓     |            |       |       | ✓     |
+-----------------------------+-------+-------+-------+------------+-------+-------+-------+
| Endianness conversion       | ✓ (2) |       |       |            |       |       |       |
+-----------------------------+-------+-------+-------+------------+-------+-------+-------+
| Custom schema metadata      | ✓     | ✓     | ✓     |            |  ✓    |  ✓    | ✓     |
+-----------------------------+-------+-------+-------+------------+-------+-------+-------+

Notes:

* \(1) Delta dictionaries not supported on nested dictionaries

* \(2) Data with non-native endianness can be byte-swapped automatically when reading.

* \(3) LZ4 Codec currently is quite inefficient. ARROW-11901 tracks improving performance.

.. seealso::
   The :ref:`format-ipc` specification.

.. _status-flight-rpc:

Flight RPC
==========

.. note:: Flight RPC is still experimental.

+--------------------------------------------+-------+-------+-------+------------+-------+-------+-------+
| Flight RPC Transport                       | C++   | Java  | Go    | JavaScript | C#    | Rust  | Julia |
+============================================+=======+=======+=======+============+=======+=======+=======+
| gRPC_ transport (grpc:, grpc+tcp:)         | ✓     | ✓     | ✓     |            | ✓     |       |       |
+--------------------------------------------+-------+-------+-------+------------+-------+-------+-------+
| gRPC domain socket transport (grpc+unix:)  | ✓     | ✓     | ✓     |            | ✓     |       |       |
+--------------------------------------------+-------+-------+-------+------------+-------+-------+-------+
| gRPC + TLS transport (grpc+tls:)           | ✓     | ✓     | ✓     |            | ✓     |       |       |
+--------------------------------------------+-------+-------+-------+------------+-------+-------+-------+
| UCX_ transport (ucx:)                      | ✓     |       |       |            |       |       |       |
+--------------------------------------------+-------+-------+-------+------------+-------+-------+-------+

Supported features in the gRPC transport:

+--------------------------------------------+-------+-------+-------+------------+-------+-------+-------+
| Flight RPC Feature                         | C++   | Java  | Go    | JavaScript | C#    | Rust  | Julia |
+============================================+=======+=======+=======+============+=======+=======+=======+
| All RPC methods                            | ✓     | ✓     | ✓     |            | × (1) | ✓     |       |
+--------------------------------------------+-------+-------+-------+------------+-------+-------+-------+
| Authentication handlers                    | ✓     | ✓     | ✓     |            | ✓ (2) | ✓     |       |
+--------------------------------------------+-------+-------+-------+------------+-------+-------+-------+
| Call timeouts                              | ✓     | ✓     | ✓     |            |       | ✓     |       |
+--------------------------------------------+-------+-------+-------+------------+-------+-------+-------+
| Call cancellation                          | ✓     | ✓     | ✓     |            |       | ✓     |       |
+--------------------------------------------+-------+-------+-------+------------+-------+-------+-------+
| Concurrent client calls (3)                | ✓     | ✓     | ✓     |            | ✓     | ✓     |       |
+--------------------------------------------+-------+-------+-------+------------+-------+-------+-------+
| Custom middleware                          | ✓     | ✓     | ✓     |            |       | ✓     |       |
+--------------------------------------------+-------+-------+-------+------------+-------+-------+-------+
| RPC error codes                            | ✓     | ✓     | ✓     |            | ✓     | ✓     |       |
+--------------------------------------------+-------+-------+-------+------------+-------+-------+-------+

Supported features in the UCX transport:

+--------------------------------------------+-------+-------+-------+------------+-------+-------+-------+
| Flight RPC Feature                         | C++   | Java  | Go    | JavaScript | C#    | Rust  | Julia |
+============================================+=======+=======+=======+============+=======+=======+=======+
| All RPC methods                            | × (4) |       |       |            |       |       |       |
+--------------------------------------------+-------+-------+-------+------------+-------+-------+-------+
| Authentication handlers                    |       |       |       |            |       |       |       |
+--------------------------------------------+-------+-------+-------+------------+-------+-------+-------+
| Call timeouts                              |       |       |       |            |       |       |       |
+--------------------------------------------+-------+-------+-------+------------+-------+-------+-------+
| Call cancellation                          |       |       |       |            |       |       |       |
+--------------------------------------------+-------+-------+-------+------------+-------+-------+-------+
| Concurrent client calls                    | ✓ (5) |       |       |            |       |       |       |
+--------------------------------------------+-------+-------+-------+------------+-------+-------+-------+
| Custom middleware                          |       |       |       |            |       |       |       |
+--------------------------------------------+-------+-------+-------+------------+-------+-------+-------+
| RPC error codes                            | ✓     |       |       |            |       |       |       |
+--------------------------------------------+-------+-------+-------+------------+-------+-------+-------+

Notes:

* \(1) No support for handshake or DoExchange.
* \(2) Support using AspNetCore authentication handlers.
* \(3) Whether a single client can support multiple concurrent calls.
* \(4) Only support for DoExchange, DoGet, DoPut, and GetFlightInfo.
* \(5) Each concurrent call is a separate connection to the server
  (unlike gRPC where concurrent calls are multiplexed over a single
  connection). This will generally provide better throughput but
  consumes more resources both on the server and the client.

.. seealso::
   The :ref:`flight-rpc` specification.

.. _gRPC: https://grpc.io/
.. _UCX: https://openucx.org/

C Data Interface
================

+-----------------------------+-----+--------+---+------+----+------+--------+------+-------+
| Feature                     | C++ | Python | R | Rust | Go | Java | C/GLib | Ruby | Julia |
|                             |     |        |   |      |    |      |        |      |       |
+=============================+=====+========+===+======+====+======+========+======+=======+
| Schema export               | ✓   | ✓      | ✓ | ✓    | ✓  | ✓    | ✓      | ✓    |       |
+-----------------------------+-----+--------+---+------+----+------+--------+------+-------+
| Array export                | ✓   | ✓      | ✓ | ✓    | ✓  | ✓    | ✓      | ✓    |       |
+-----------------------------+-----+--------+---+------+----+------+--------+------+-------+
| Schema import               | ✓   | ✓      | ✓ | ✓    | ✓  | ✓    | ✓      | ✓    |       |
+-----------------------------+-----+--------+---+------+----+------+--------+------+-------+
| Array import                | ✓   | ✓      | ✓ | ✓    | ✓  | ✓    | ✓      | ✓    |       |
+-----------------------------+-----+--------+---+------+----+------+--------+------+-------+

.. seealso::
   The :ref:`C Data Interface <c-data-interface>` specification.


C Stream Interface
==================

+-----------------------------+-----+--------+---+------+----+------+--------+------+-------+
| Feature                     | C++ | Python | R | Rust | Go | Java | C/GLib | Ruby | Julia |
|                             |     |        |   |      |    |      |        |      |       |
+=============================+=====+========+===+======+====+======+========+======+=======+
| Stream export               | ✓   | ✓      | ✓ | ✓    |    |      | ✓      | ✓    |       |
+-----------------------------+-----+--------+---+------+----+------+--------+------+-------+
| Stream import               | ✓   | ✓      | ✓ | ✓    | ✓  |      | ✓      | ✓    |       |
+-----------------------------+-----+--------+---+------+----+------+--------+------+-------+

.. seealso::
   The :ref:`C Stream Interface <c-stream-interface>` specification.


Third-Party Data Formats
========================

+-----------------------------+---------+---------+-------+------------+-------+---------+-------+
| Format                      | C++     | Java    | Go    | JavaScript | C#    | Rust    | Julia |
|                             |         |         |       |            |       |         |       |
+=============================+=========+=========+=======+============+=======+=========+=======+
| Avro                        |         | R       |       |            |       |         |       |
+-----------------------------+---------+---------+-------+------------+-------+---------+-------+
| CSV                         | R/W     |         | R/W   |            |       | R/W     | R/W   |
+-----------------------------+---------+---------+-------+------------+-------+---------+-------+
| ORC                         | R/W     | R (2)   |       |            |       |         |       |
+-----------------------------+---------+---------+-------+------------+-------+---------+-------+
| Parquet                     | R/W     | R (3)   | R/W   |            |       | R/W (1) |       |
+-----------------------------+---------+---------+-------+------------+-------+---------+-------+

Notes:

* *R* = Read supported

* *W* = Write supported

* \(1) Nested read/write not supported.

* \(2) Through JNI bindings. (Provided by ``org.apache.arrow.orc:arrow-orc``)

* \(3) Through JNI bindings to Arrow C++ Datasets. (Provided by ``org.apache.arrow:arrow-dataset``)
