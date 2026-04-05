# Awesome Serialization & Deserialization [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of data serialization formats, libraries, tools, and resources across programming languages and use cases.

**Serialization** is the process of converting data structures or objects into a format suitable for storage or transmission. **Deserialization** reconstructs the original data from the serialized format. These processes are foundational to data persistence, network communication, distributed systems, and cross-platform interoperability.

## Contents

- [Serialization Formats](#serialization-formats)
  - [Text-Based Formats](#text-based-formats)
  - [Binary Formats](#binary-formats)
  - [Zero-Copy & High-Performance Formats](#zero-copy--high-performance-formats)
  - [Domain-Specific Formats](#domain-specific-formats)
- [Libraries by Language](#libraries-by-language)
  - [Python](#python)
  - [Java & JVM](#java--jvm)
  - [JavaScript & TypeScript](#javascript--typescript)
  - [C & C++](#c--c)
  - [Rust](#rust)
  - [Go](#go)
  - [C# & .NET](#c--net)
  - [Ruby](#ruby)
  - [PHP](#php)
  - [Swift](#swift)
- [Use Cases & Applications](#use-cases--applications)
  - [APIs & Network Services](#apis--network-services)
  - [Big Data & Analytics](#big-data--analytics)
  - [Machine Learning & AI](#machine-learning--ai)
  - [Configuration Files](#configuration-files)
  - [Security-Focused Serialization](#security-focused-serialization)
  - [Scientific & Research](#scientific--research)
  - [Graph Data](#graph-data)
  - [Workflow Management](#workflow-management)
  - [Schema Evolution](#schema-evolution)
  - [Security Considerations](#security-considerations)
  - [Known Vulnerabilities](#known-vulnerabilities)
  - [Documented CVEs](#documented-cves)
  - [Mitigation Strategies](#mitigation-strategies)
- [Standards & Specifications](#standards--specifications)
  - [IETF RFC Standards](#ietf-rfc-standards)
  - [W3C Standards](#w3c-standards)
  - [ISO Standards](#iso-standards)
- [Tools & Utilities](#tools--utilities)
- [Learning Resources](#learning-resources)
  - [Technical Documentation](#technical-documentation)
  - [Research Papers](#research-papers)
- [Related Awesome Lists](#related-awesome-lists)

---

## Serialization Formats

### Text-Based Formats

Human-readable formats suitable for debugging, configuration, and API communication.

| Format | Full Name | Standard | Human-Readable | Schema Support | Binary Types | Links |
|--------|-----------|----------|----------------|----------------|--------------|-------|
| **[JSON](https://www.json.org/)** | JavaScript Object Notation | RFC 8259 | ✅ | ❌ (JSON Schema separate) | ❌ | [RFC 8259](https://datatracker.ietf.org/doc/html/rfc8259) |
| **[XML](https://www.w3.org/XML/)** | Extensible Markup Language | W3C Recommendation | ✅ | ✅ (XSD) | ❌ (Base64) | [W3C XML](https://www.w3.org/XML/) |
| **[YAML](https://yaml.org/)** | YAML Ain't Markup Language | YAML 1.2.2 Spec | ✅ | ❌ | ❌ | [Specification](https://yaml.org/spec/1.2.2/) |
| **[TOML](https://toml.io/)** | Tom's Obvious Minimal Language | TOML 1.0.0 | ✅ | ❌ | ❌ | [Specification](https://toml.io/en/v1.0.0) |
| **[CSV](https://en.wikipedia.org/wiki/Comma-separated_values)** | Comma-Separated Values | RFC 4180 | ✅ | ❌ | ❌ | [RFC 4180](https://datatracker.ietf.org/doc/html/rfc4180) |
| **[JSON5](https://json5.org/)** | JSON for Humans | JSON5 Spec | ✅ | ❌ | ❌ | [Specification](https://json5.org/) |
| **[JSONL/NDJSON](http://jsonlines.org/)** | JSON Lines | Convention | ✅ | ❌ | ❌ | [Specification](http://jsonlines.org/) |
| **[ION](https://amzn.github.io/ion-docs/)** | Amazon Ion | Amazon Ion Spec | ✅ (text mode) | ❌ | ✅ (binary mode) | [GitHub](https://github.com/amazon-ion/ion-docs) |

### Binary Formats

Compact formats optimized for performance, storage efficiency, and network transmission.

| Format | Developer/Org | Schema Required | Cross-Language | Schema Evolution | Links |
|--------|---------------|-----------------|----------------|------------------|-------|
| **[Protocol Buffers](https://developers.google.com/protocol-buffers)** | Google | ✅ (.proto) | ✅ (20+ languages) | ✅ (backward/forward) | [GitHub](https://github.com/protocolbuffers/protobuf) |
| **[Apache Avro](https://avro.apache.org/)** | Apache Software Foundation | ✅ (JSON schema) | ✅ (Java, Python, C++, etc.) | ✅ (built-in) | [Website](https://avro.apache.org/) |
| **[Apache Thrift](https://thrift.apache.org/)** | Apache (originally Facebook) | ✅ (.thrift) | ✅ (28+ languages) | ⚠️ (limited) | [Website](https://thrift.apache.org/) |
| **[MessagePack](https://msgpack.org/)** | Sadayuki Furuhashi | ❌ | ✅ (70+ languages) | ❌ | [Website](https://msgpack.org/) |
| **[CBOR](https://cbor.io/)** | IETF | ❌ | ✅ (50+ languages) | ❌ | [RFC 8949](https://datatracker.ietf.org/doc/html/rfc8949) |
| **[BSON](https://bsonspec.org/)** | MongoDB | ❌ | ✅ (20+ languages) | ❌ | [Specification](https://bsonspec.org/) |
| **[Smile](https://github.com/FasterXML/smile-format-specification)** | FasterXML | ❌ | ✅ (Java, others) | ❌ | [Spec](https://github.com/FasterXML/smile-format-specification) |
| **[Hessian](http://hessian.caucho.com/)** | Caucho Technology | ❌ | ✅ (Java, Python, C#, etc.) | ❌ | [Website](http://hessian.caucho.com/) |

### Zero-Copy & High-Performance Formats

Formats enabling direct memory access without intermediate parsing/unpacking steps.

| Format | Developer | Zero-Copy | Schema Required | Memory Mapping | Primary Use Case | Links |
|--------|-----------|-----------|-----------------|----------------|------------------|-------|
| **[Apache Arrow](https://arrow.apache.org/)** | Apache Software Foundation | ✅ | ❌ (implicit) | ✅ | In-memory analytics, DataFrame interchange | [GitHub](https://github.com/apache/arrow) |
| **[FlatBuffers](https://flatbuffers.dev/)** | Google | ✅ | ✅ (.fbs) | ✅ | Gaming, mobile apps, low-latency systems | [GitHub](https://github.com/google/flatbuffers) |
| **[Cap'n Proto](https://capnproto.org/)** | Kenton Varda (Sandstorm) | ✅ | ✅ (.capnp) | ✅ | High-performance RPC, distributed systems | [GitHub](https://github.com/capnproto/capnproto) |
| **[Bebop](https://github.com/RainwayApp/bebop)** | Rainway | ✅ | ✅ (.bop) | ✅ | Game streaming, real-time applications | [GitHub](https://github.com/RainwayApp/bebop) |

### Domain-Specific Formats

Formats designed for specific industries, data types, or application domains.

| Format | Domain | Type | Columnar | Schema | Description | Links |
|--------|--------|------|----------|--------|-------------|-------|
| **[Parquet](https://parquet.apache.org/)** | Big Data Analytics | Binary | ✅ | ✅ | Columnar storage for Hadoop ecosystem | [Website](https://parquet.apache.org/) |
| **[ORC](https://orc.apache.org/)** | Big Data (Hive) | Binary | ✅ | ✅ | Optimized Row Columnar format | [Website](https://orc.apache.org/) |
| **[HDF5](https://www.hdfgroup.org/solutions/hdf5/)** | Scientific Computing | Binary | ❌ | ✅ | Hierarchical Data Format for large datasets | [Website](https://www.hdfgroup.org/solutions/hdf5/) |
| **[ONNX](https://onnx.ai/)** | Machine Learning | Binary (Protobuf) | ❌ | ✅ | Open Neural Network Exchange format | [Website](https://onnx.ai/) |
| **[GGUF](https://github.com/ggerganov/ggml/blob/master/docs/gguf.md)** | LLM Inference | Binary | ❌ | ✅ | Quantized model format for llama.cpp | [GitHub](https://github.com/ggerganov/ggml) |
| **[ASN.1](https://www.itu.int/en/ITU-T/asn1/)** | Telecommunications | Binary/Text | ❌ | ✅ | Abstract Syntax Notation One (ITU-T standard) | [ITU](https://www.itu.int/en/ITU-T/asn1/) |
| **[NetCDF](https://www.unidata.ucar.edu/software/netcdf/)** | Earth/Climate Science | Binary | ✅ | ✅ | Network Common Data Form | [Website](https://www.unidata.ucar.edu/software/netcdf/) |
| **[Delta Lake](https://delta.io/)** | Data Lakes | Binary (Parquet-based) | ✅ | ✅ | ACID transactions on data lakes | [Website](https://delta.io/) |
| **[Apache Iceberg](https://iceberg.apache.org/)** | Data Lakes | Binary | ✅ | ✅ | Open table format for large datasets | [Website](https://iceberg.apache.org/) |
| **[Lance](https://lancedb.github.io/lance/)** | ML/Data Science | Binary | ✅ | ✅ | Columnar format optimized for ML workloads | [GitHub](https://github.com/lancedb/lance) |
| **[SavedModel](https://www.tensorflow.org/guide/saved_model)** | Deep Learning (TensorFlow) | Binary (Protobuf) | ❌ | ✅ | TensorFlow model serialization format | [Docs](https://www.tensorflow.org/guide/saved_model) |
| **[CoreML](https://developer.apple.com/machine-learning/)** | Machine Learning (Apple) | Binary (Protobuf) | ❌ | ✅ | Apple's on-device ML model format | [Docs](https://developer.apple.com/documentation/coreml) |

---

## Libraries by Language

### Python

| Library | Formats | License | Description | Links |
|---------|---------|---------|-------------|-------|
| **[json](https://docs.python.org/3/library/json.html)** | JSON | PSF | Built-in JSON encoder/decoder (stdlib) | [Docs](https://docs.python.org/3/library/json.html) |
| **[pickle](https://docs.python.org/3/library/pickle.html)** | Python-specific | PSF | Python object serialization (stdlib) ⚠️ | [Docs](https://docs.python.org/3/library/pickle.html) |
| **[msgpack-python](https://pypi.org/project/msgpack/)** | MessagePack | Apache 2.0 | MessagePack implementation | [PyPI](https://pypi.org/project/msgpack/) |
| **[srsly](https://github.com/explosion/srsly)** | JSON, MsgPack, YAML | MIT | High-performance serialization wrapper | [GitHub](https://github.com/explosion/srsly) |
| **[avro-python3](https://pypi.org/project/avro-python3/)** | Avro | Apache 2.0 | Apache Avro implementation | [PyPI](https://pypi.org/project/avro-python3/) |
| **[protobuf](https://pypi.org/project/protobuf/)** | Protocol Buffers | BSD-3 | Official Google protobuf | [PyPI](https://pypi.org/project/protobuf/) |
| **[pyarrow](https://arrow.apache.org/docs/python/)** | Arrow, Parquet, Feather | Apache 2.0 | Apache Arrow Python bindings | [Docs](https://arrow.apache.org/docs/python/) |
| **[pyyaml](https://github.com/yaml/pyyaml)** | YAML | MIT | YAML parser and emitter | [GitHub](https://github.com/yaml/pyyaml) |
| **[orjson](https://github.com/ijl/orjson)** | JSON | Apache 2.0/MIT | Fast, correct Python JSON (Rust-based) | [GitHub](https://github.com/ijl/orjson) |
| **[ujson](https://github.com/ultrajson/ultrajson)** | JSON | BSD-3 | Ultra-fast JSON encoder/decoder (C-based) | [GitHub](https://github.com/ultrajson/ultrajson) |
| **[safetensors](https://github.com/huggingface/safetensors)** | Custom | Apache 2.0 | Secure ML tensor format | [GitHub](https://github.com/huggingface/safetensors) |

### Java & JVM

| Library | Formats | License | Description | Links |
|---------|---------|---------|-------------|-------|
| **[Jackson](https://github.com/FasterXML/jackson)** | JSON, Smile, CBOR, YAML, XML | Apache 2.0 | Most widely-used Java serialization | [GitHub](https://github.com/FasterXML/jackson) |
| **[Gson](https://github.com/google/gson)** | JSON | Apache 2.0 | Google's JSON library for Java | [GitHub](https://github.com/google/gson) |
| **[Moshi](https://github.com/square/moshi)** | JSON | Apache 2.0 | Modern JSON library by Square | [GitHub](https://github.com/square/moshi) |
| **[dsl-json](https://github.com/ngs-doo/dsl-json)** | JSON | BSD-3 | High-performance Java JSON library | [GitHub](https://github.com/ngs-doo/dsl-json) |
| **[Kryo](https://github.com/EsotericSoftware/kryo)** | Binary | BSD-3 | Fast, efficient Java serialization | [GitHub](https://github.com/EsotericSoftware/kryo) |
| **[protobuf-java](https://github.com/protocolbuffers/protobuf)** | Protocol Buffers | BSD-3 | Official Java protobuf | [GitHub](https://github.com/protocolbuffers/protobuf) |
| **[Avro Java](https://avro.apache.org/docs/current/gettingstartedjava.html)** | Avro | Apache 2.0 | Apache Avro for Java | [Docs](https://avro.apache.org/docs/current/gettingstartedjava.html) |

### JavaScript & TypeScript

| Library | Formats | License | Description | Links |
|---------|---------|---------|-------------|-------|
| **[JSON (native)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON)** | JSON | ECMAScript Spec | Built-in JSON support (ES5+) | [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON) |
| **[BSON.js](https://github.com/mongodb/js-bson)** | BSON | Apache 2.0 | BSON implementation in JavaScript | [GitHub](https://github.com/mongodb/js-bson) |
| **[msgpack-javascript](https://github.com/msgpack/msgpack-javascript)** | MessagePack | Apache 2.0 | MessagePack for JavaScript | [GitHub](https://github.com/msgpack/msgpack-javascript) |
| **[avsc](https://github.com/mtth/avsc)** | Avro | BSD-3 | Zero-dependency Avro implementation | [GitHub](https://github.com/mtth/avsc) |
| **[protobuf.js](https://github.com/protobufjs/protobuf.js)** | Protocol Buffers | BSD-3 | Protocol Buffers for JavaScript | [GitHub](https://github.com/protobufjs/protobuf.js) |
| **[schemapack](https://github.com/phretaddin/schemapack)** | Custom binary | MIT | Schema-based binary encoding | [GitHub](https://github.com/phretaddin/schemapack) |
| **[cbor-js](https://github.com/paroga/cbor-js)** | CBOR | MIT | CBOR implementation | [GitHub](https://github.com/paroga/cbor-js) |
| **[msgpackr](https://github.com/kriszyp/msgpackr)** | MessagePack | MIT | High-performance MessagePack | [GitHub](https://github.com/kriszyp/msgpackr) |

### C & C++

| Library | Formats | License | Description | Links |
|---------|---------|---------|-------------|-------|
| **[RapidJSON](https://github.com/Tencent/rapidjson)** | JSON | MIT | Fast C++ JSON parser/generator | [GitHub](https://github.com/Tencent/rapidjson) |
| **[nlohmann/json](https://github.com/nlohmann/json)** | JSON | MIT | JSON for Modern C++ | [GitHub](https://github.com/nlohmann/json) |
| **[simdjson](https://github.com/simdjson/simdjson)** | JSON | Apache 2.0 | Gigabytes/sec JSON parsing (SIMD) | [GitHub](https://github.com/simdjson/simdjson) |
| **[ArduinoJson](https://arduinojson.org/)** | JSON | MIT | JSON library for embedded C++ | [Website](https://arduinojson.org/) |
| **[BitSerializer](https://github.com/PavelYevstifeev/bitserializer)** | JSON, XML, YAML, CSV, MsgPack | MIT | Multi-format C++ serialization | [GitHub](https://github.com/PavelYevstifeev/bitserializer) |
| **[Bitsery](https://github.com/fraillt/bitsery)** | Binary | MIT | Header-only binary serialization | [GitHub](https://github.com/fraillt/bitsery) |
| **[Jansson](https://github.com/akheron/jansson)** | JSON | MIT | C library for JSON | [GitHub](https://github.com/akheron/jansson) |
| **[jsmn](https://github.com/zserge/jsmn)** | JSON | MIT | Minimalistic JSON parser for C | [GitHub](https://github.com/zserge/jsmn) |
| **[protobuf-c](https://github.com/protobuf-c/protobuf-c)** | Protocol Buffers | BSD-2 | Protobuf implementation for C | [GitHub](https://github.com/protobuf-c/protobuf-c) |
| **[flatbuffers](https://github.com/google/flatbuffers)** | FlatBuffers | Apache 2.0 | Official FlatBuffers C++ | [GitHub](https://github.com/google/flatbuffers) |

### Rust

| Library | Formats | License | Description | Links |
|---------|---------|---------|-------------|-------|
| **[Serde](https://serde.rs/)** | Multiple (via adapters) | Apache 2.0/MIT | Serialization framework for Rust | [Website](https://serde.rs/) |
| **[serde_json](https://github.com/serde-rs/json)** | JSON | Apache 2.0/MIT | Serde JSON adapter | [GitHub](https://github.com/serde-rs/json) |
| **[bincode](https://github.com/bincode-org/bincode)** | Binary | MIT | Binary encoder for Rust | [GitHub](https://github.com/bincode-org/bincode) |
| **[rmp-serde](https://github.com/3Hren/msgpack-rust)** | MessagePack | MIT | MessagePack for Rust | [GitHub](https://github.com/3Hren/msgpack-rust) |
| **[quick-xml](https://github.com/tafia-eu/quick-xml)** | XML | MIT | High-performance XML parser | [GitHub](https://github.com/tafia-eu/quick-xml) |
| **[toml-rs](https://github.com/toml-rs/toml)** | TOML | Apache 2.0/MIT | TOML encoder/decoder | [GitHub](https://github.com/toml-rs/toml) |
| **[postcard](https://github.com/jamesmunns/postcard)** | Binary | Apache 2.0/MIT | Compact binary for embedded | [GitHub](https://github.com/jamesmunns/postcard) |
| **[capnp](https://capnproto.org/)** | Cap'n Proto | MIT | Official Cap'n Proto for Rust | [Website](https://capnproto.org/) |

### Go

| Library | Formats | License | Description | Links |
|---------|---------|---------|-------------|-------|
| **[encoding/json](https://pkg.go.dev/encoding/json)** | JSON | BSD-3 | Built-in JSON package (stdlib) | [Docs](https://pkg.go.dev/encoding/json) |
| **[gob](https://pkg.go.dev/encoding/gob)** | GOB | BSD-3 | Go's native binary format (stdlib) | [Docs](https://pkg.go.dev/encoding/gob) |
| **[protobuf-go](https://github.com/protocolbuffers/protobuf-go)** | Protocol Buffers | BSD-3 | Official Go protobuf | [GitHub](https://github.com/protocolbuffers/protobuf-go) |
| **[vmihailenco/msgpack](https://github.com/vmihailenco/msgpack)** | MessagePack | MIT | MessagePack for Go | [GitHub](https://github.com/vmihailenco/msgpack) |
| **[go-yaml/yaml](https://github.com/go-yaml/yaml)** | YAML | Apache 2.0/MIT | YAML support for Go | [GitHub](https://github.com/go-yaml/yaml) |
| **[segmentio/encoding](https://github.com/segmentio/encoding)** | JSON, Avro | MIT | High-performance encoding | [GitHub](https://github.com/segmentio/encoding) |
| **[json-iterator/go](https://github.com/json-iterator/go)** | JSON | MIT | Drop-in JSON replacement | [GitHub](https://github.com/json-iterator/go) |

### C# & .NET

| Library | Formats | License | Description | Links |
|---------|---------|---------|-------------|-------|
| **[System.Text.Json](https://docs.microsoft.com/en-us/dotnet/api/system.text.json)** | JSON | MIT | Built-in .NET JSON (.NET Core 3.0+) | [Docs](https://docs.microsoft.com/en-us/dotnet/api/system.text.json) |
| **[Newtonsoft.Json](https://www.newtonsoft.com/json)** | JSON | MIT | Most popular .NET JSON library | [Website](https://www.newtonsoft.com/json) |
| **[protobuf-net](https://github.com/protobuf-net/protobuf-net)** | Protocol Buffers | Apache 2.0 | Protobuf for .NET | [GitHub](https://github.com/protobuf-net/protobuf-net) |
| **[MessagePack-CSharp](https://github.com/MessagePack-CSharp/MessagePack-CSharp)** | MessagePack | MIT | Fast MessagePack for C# | [GitHub](https://github.com/MessagePack-CSharp/MessagePack-CSharp) |
| **[ZeroFormatter](https://github.com/neuecc/ZeroFormatter)** | Binary | MIT | Fastest deserialization for .NET | [GitHub](https://github.com/neuecc/ZeroFormatter) |

### Ruby

| Library | Formats | License | Description | Links |
|---------|---------|---------|-------------|-------|
| **[json](https://ruby-doc.org/stdlib/libdoc/json/rdoc/JSON.html)** | JSON | Ruby | Built-in JSON (stdlib) | [Docs](https://ruby-doc.org/stdlib/libdoc/json/rdoc/JSON.html) |
| **[oj](https://github.com/ohler55/oj)** | JSON | MIT | Optimized JSON parser (C extension) | [GitHub](https://github.com/ohler55/oj) |
| **[MultiJSON](https://github.com/intridea/multi_json)** | JSON | MIT | Common interface for JSON libs | [GitHub](https://github.com/intridea/multi_json) |
| **[msgpack-ruby](https://github.com/msgpack/msgpack-ruby)** | MessagePack | Apache 2.0 | MessagePack for Ruby | [GitHub](https://github.com/msgpack/msgpack-ruby) |

### PHP

| Library | Formats | License | Description | Links |
|---------|---------|---------|-------------|-------|
| **[json_encode/decode](https://www.php.net/manual/en/book.json.php)** | JSON | PHP | Built-in PHP JSON (stdlib) | [Docs](https://www.php.net/manual/en/book.json.php) |
| **[webmozart/json](https://github.com/webmozarts/json)** | JSON | MIT | JSON validation library | [GitHub](https://github.com/webmozarts/json) |

### Swift

| Library | Formats | License | Description | Links |
|---------|---------|---------|-------------|-------|
| **[Codable](https://developer.apple.com/documentation/swift/codable)** | JSON, Plist | Apple | Built-in Swift serialization (Swift 4+) | [Docs](https://developer.apple.com/documentation/swift/codable) |
| **[SwiftyJSON](https://github.com/SwiftyJSON/SwiftyJSON)** | JSON | MIT | Easier JSON handling | [GitHub](https://github.com/SwiftyJSON/SwiftyJSON) |
| **[MessagePack.swift](https://github.com/chriseidhof/MessagePack.swift)** | MessagePack | MIT | MessagePack for Swift | [GitHub](https://github.com/chriseidhof/MessagePack.swift) |

---

## Use Cases & Applications

### APIs & Network Services

| Technology | Format(s) | Type | Schema | Production Users | Links |
|------------|-----------|------|--------|------------------|-------|
| **[gRPC](https://grpc.io/)** | Protocol Buffers | RPC framework | ✅ | Netflix, Cisco, Uber, Twitter | [Website](https://grpc.io/) |
| **[RSocket](https://rsocket.io/)** | Various | Reactive protocol | ✅ | Netflix, Facebook | [Website](https://rsocket.io/) |
| **[Connect](https://connect.build/)** | Protobuf, JSON | RPC framework | ✅ | buf.build clients | [Website](https://connect.build/) |
| **[CloudEvents](https://cloudevents.io/)** | JSON, Protobuf, Avro | Event specification | ✅ | CNCF projects | [Website](https://cloudevents.io/) |
| **[AsyncAPI](https://www.asyncapi.com/)** | JSON, YAML | Event-driven API spec | ⚠️ | Event-driven architectures | [Website](https://www.asyncapi.com/) |

### Big Data & Analytics

| Technology | Format(s) | Storage Type | Compression | Ecosystem | Links |
|------------|-----------|--------------|-------------|-----------|-------|
| **[Apache Parquet](https://parquet.apache.org/)** | Parquet | Columnar | Snappy, Gzip, LZO | Hadoop, Spark, Presto | [Website](https://parquet.apache.org/) |
| **[Apache ORC](https://orc.apache.org/)** | ORC | Columnar | ZLIB, Snappy | Hive, Spark SQL | [Website](https://orc.apache.org/) |
| **[Apache Arrow](https://arrow.apache.org/)** | Arrow, Feather | In-memory columnar | N/A | Pandas, Polars, DuckDB | [Website](https://arrow.apache.org/) |
| **[Apache Avro](https://avro.apache.org/)** | Avro | Row-based | Deflate | Kafka, Hadoop | [Website](https://avro.apache.org/) |
| **[Delta Lake](https://delta.io/)** | Parquet-based | Columnar + transaction log | Snappy, ZSTD | Databricks, Spark | [Website](https://delta.io/) |
| **[Apache Iceberg](https://iceberg.apache.org/)** | Parquet/ORC/Arrow | Columnar + metadata | Various | Spark, Flink, Trino | [Website](https://iceberg.apache.org/) |

### Machine Learning & AI

| Technology | Format | Base Format | Framework Support | Zero-Copy | Links |
|------------|--------|-------------|-------------------|-----------|-------|
| **[ONNX](https://onnx.ai/)** | ONNX | Protobuf | PyTorch, TensorFlow, scikit-learn | ❌ | [Website](https://onnx.ai/) |
| **[TensorFlow SavedModel](https://www.tensorflow.org/guide/saved_model)** | SavedModel | Protobuf | TensorFlow | ❌ | [Docs](https://www.tensorflow.org/guide/saved_model) |
| **[CoreML](https://developer.apple.com/machine-learning/)** | CoreML | Protobuf | Core ML Tools | ❌ | [Docs](https://developer.apple.com/machine-learning/) |
| **[GGUF](https://github.com/ggerganov/ggml/blob/master/docs/gguf.md)** | GGUF | Custom | llama.cpp, Ollama | ✅ (mmap) | [GitHub](https://github.com/ggerganov/ggml) |
| **[safetensors](https://github.com/huggingface/safetensors)** | Safetensors | Custom | PyTorch, TensorFlow, JAX | ✅ (mmap) | [GitHub](https://github.com/huggingface/safetensors) |
| **[MLIR](https://mlir.llvm.org/)** | MLIR | Text/Binary | LLVM, XLA, IREE | ❌ | [Website](https://mlir.llvm.org/) |
| **[Lance](https://lancedb.github.io/lance/)** | Lance | Custom | LanceDB, Pandas | ✅ | [GitHub](https://github.com/lancedb/lance) |

**Agentic AI & LLM Protocols:**

| Protocol/Format | Type | Serialization | Status | Links |
|-----------------|------|---------------|--------|-------|
| **[MCP](https://modelcontextprotocol.io/)** | AI context protocol | JSON-RPC | v1.0 (2024) | [Website](https://modelcontextprotocol.io/) |
| **[A2A](https://google.github.io/A2A/)** | Agent interoperability | JSON | Draft | [GitHub](https://github.com/google/A2A) |
| **[BAML](https://www.boundaryml.com/baml)** | Structured LLM output | Custom DSL | Active development | [Website](https://www.boundaryml.com/baml) |

### Configuration Files

| Format | Indentation | Comments | Multi-line Strings | Data Types | Common Usage | Links |
|--------|-------------|----------|-------------------|------------|--------------|-------|
| **[YAML](https://yaml.org/)** | Significant whitespace | ✅ | ✅ | Rich (maps, sequences, scalars) | Kubernetes, Docker Compose, GitHub Actions | [Specification](https://yaml.org/spec/1.2.2/) |
| **[TOML](https://toml.io/)** | Section-based | ✅ | ✅ | Basic types, arrays, dates | Cargo, Poetry, Hugo | [Specification](https://toml.io/) |
| **[JSON](https://www.json.org/)** | Flexible | ❌ | ❌ | Objects, arrays, strings, numbers, booleans, null | VS Code, TypeScript, npm | [RFC 8259](https://datatracker.ietf.org/doc/html/rfc8259) |
| **[JSON5](https://json5.org/)** | Flexible | ✅ | ✅ | Extended JSON | Development configs | [Specification](https://json5.org/) |
| **[CUE](https://cuelang.org/)** | Flexible | ✅ | ✅ | Types + values | Infrastructure as Code | [Website](https://cuelang.org/) |
| **[Pkl](https://pkl-lang.org/)** | Flexible | ✅ | ✅ | Rich (classes, functions) | Apple ecosystem | [Website](https://pkl-lang.org/) |
| **[KCL](https://kcl-lang.io/)** | Flexible | ✅ | ✅ | Constraint-based | Cloud-native config | [Website](https://kcl-lang.io/) |
| **[HCL](https://github.com/hashicorp/hcl)** | Block-based | ✅ | ✅ | Blocks, attributes, lists | Terraform, Vault | [GitHub](https://github.com/hashicorp/hcl) |

### Security-Focused Serialization

| Technology | Format | Security Property | Description | Links |
|------------|--------|-------------------|-------------|-------|
| **[safetensors](https://github.com/huggingface/safetensors)** | Binary | No arbitrary code execution | Header-based format with only tensor data; prevents pickle RCE | [GitHub](https://github.com/huggingface/safetensors) |
| **[COSE](https://datatracker.ietf.org/doc/html/rfc8152)** | CBOR-based | Cryptographic signatures | CBOR Object Signing and Encryption | [RFC 8152](https://datatracker.ietf.org/doc/html/rfc8152) |
| **[PASETO](https://paseto.io/)** | JSON/Binary | Tamper-proof tokens | Platform-Agnostic SEcure TOkens (JWT alternative) | [Website](https://paseto.io/) |
| **[SealedObject](https://docs.oracle.com/javase/8/docs/api/java/security/SealedObject.html)** | Java Serialized | Encryption | Encrypted Java objects using cryptographic seals | [Java Docs](https://docs.oracle.com/javase/8/docs/api/java/security/SealedObject.html) |
| **[Capsule (Java)](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/io/ObjectInputFilter.html)** | Java Serialized | Object filtering | ObjectInputFilter for controlling deserialization | [Java Docs](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/io/ObjectInputFilter.html) |

### Scientific & Research

| Format | Primary Domain | Data Model | Max Dimensions | Chunking | Parallel I/O | Links |
|--------|---------------|------------|----------------|----------|--------------|-------|
| **[HDF5](https://www.hdfgroup.org/solutions/hdf5/)** | General scientific | Hierarchical groups/datasets | Unlimited | ✅ | ✅ | [Website](https://www.hdfgroup.org/solutions/hdf5/) |
| **[NetCDF](https://www.unidata.ucar.edu/software/netcdf/)** | Climate/Earth science | Self-describing arrays | 7 (conventional) | ✅ | ✅ | [Website](https://www.unidata.ucar.edu/software/netcdf/) |
| **[Zarr](https://zarr.dev/)** | Earth science, biology | Chunked N-D arrays | Unlimited | ✅ | ✅ | [Website](https://zarr.dev/) |
| **[ASDF](https://asdf-standard.readthedocs.io/)** | Astronomy | Tree + binary blocks | Unlimited | ✅ | ❌ | [Docs](https://asdf-standard.readthedocs.io/) |
| **[npy/npz](https://numpy.org/doc/stable/reference/generated/numpy.lib.format.html)** | Python/NumPy | Single/multi arrays | Unlimited | ❌ | ❌ | [NumPy Docs](https://numpy.org/doc/stable/reference/generated/numpy.lib.format.html) |

### Graph Data

| Format | Type | Schema | RDF Compatible | Tools | Links |
|--------|------|--------|----------------|-------|-------|
| **[JSON-LD](https://json-ld.org/)** | Text (JSON-based) | JSON-LD Context | ✅ | JSON-LD Playground | [Website](https://json-ld.org/) |
| **[Turtle](https://www.w3.org/TR/turtle/)** | Text | RDFS/OWL | ✅ | Apache Jena | [W3C Spec](https://www.w3.org/TR/turtle/) |
| **[GraphML](http://graphml.graphdrawing.org/)** | XML-based | GraphML Schema | ❌ | yEd, Gephi | [Website](http://graphml.graphdrawing.org/) |
| **[DOT](https://graphviz.org/doc/info/lang.html)** | Text | ❌ | ❌ | Graphviz | [Graphviz](https://graphviz.org/) |
| **[GraphSON](https://tinkerpop.apache.org/docs/current/dev/io/#graphson)** | Text (JSON-based) | ❌ | ❌ | Apache TinkerPop | [Docs](https://tinkerpop.apache.org/docs/current/dev/io/#graphson) |
| **[GML](https://en.wikipedia.org/wiki/Graph_Modelling_Language)** | Text | ❌ | ❌ | NetworkX, igraph | [Wikipedia](https://en.wikipedia.org/wiki/Graph_Modelling_Language) |

### Workflow Management

| Technology | Format | Execution Engine | Domain | Links |
|------------|--------|-----------------|--------|-------|
| **[CWL](https://www.commonwl.org/)** | YAML | cwltool, Toil | Bioinformatics, data analysis | [Website](https://www.commonwl.org/) |
| **[Apache Airflow](https://airflow.apache.org/)** | Python (DAG definitions) | Airflow scheduler | General workflow orchestration | [Website](https://airflow.apache.org/) |
| **[WDL](https://openwdl.org/)** | Custom DSL | Cromwell, MiniWDL | Bioinformatics | [Website](https://openwdl.org/) |
| **[Nextflow](https://www.nextflow.io/)** | Custom DSL (Groovy-based) | Nextflow runtime | Computational pipelines | [Website](https://www.nextflow.io/) |

---

## Schema Evolution

### Compatibility Modes

| Mode | Definition | Upgrade Order | Guarantee | Use Case |
|------|------------|---------------|-----------|----------|
| **Backward** | New schema reads old data | Consumers upgrade first | ✅ Upgraded consumers process historical messages | Consumer-led upgrades |
| **Forward** | Old schema reads new data | Producers upgrade first | ✅ Legacy consumers process new messages (ignore unknown fields) | Producer-led upgrades |
| **Full** | Both backward and forward compatible | Either order | ✅ Bidirectional compatibility | Highest safety requirement |
| **None** | No compatibility checking | N/A | ❌ No guarantees | Development/testing only |

### Evolution Rules by Format

| Change | Protobuf | Avro | Thrift | Notes |
|--------|----------|------|--------|-------|
| Add optional field (with default) | ✅ Safe | ✅ Safe | ✅ Safe | Requires default value |
| Remove field | ✅ Safe (field number reserved) | ✅ Safe (reader ignores) | ⚠️ Risk | Must not reuse field numbers/names |
| Rename field | ⚠️ Risk (by name in JSON) | ❌ Breaks | ❌ Breaks | Use aliases if supported |
| Change field type | ❌ Breaks | ❌ Breaks | ❌ Breaks | Generally incompatible |
| Add required field | ❌ Breaks backward | ❌ Breaks (no default) | ❌ Breaks | Always provide default |
| Change field number (Protobuf) | ❌ Breaks | N/A | N/A | Never change field numbers |
| Change field ID (Thrift) | N/A | N/A | ❌ Breaks | Never change numeric IDs |

**Schema Registry Support:**

| Registry | Formats | Compatibility Modes | Vendor | Links |
|----------|---------|---------------------|--------|-------|
| **Confluent Schema Registry** | Avro, Protobuf, JSON Schema | Backward, Forward, Full, None | Confluent | [Docs](https://docs.confluent.io/platform/current/schema-registry/index.html) |
| **Apicurio Registry** | Avro, Protobuf, JSON Schema, XML | Multiple | Red Hat | [Website](https://www.apicur.io/) |
| **AWS Glue Schema Registry** | Avro, JSON Schema, Protobuf | Backward, Full | AWS | [Docs](https://docs.aws.amazon.com/glue/latest/dg/schema-registry.html) |

**Best Practices:**
- ✅ Always assign **default values** to new fields
- ✅ **Never reuse** field numbers/names after removal
- ✅ **Never change** field identifiers (numbers, IDs)
- ✅ Test compatibility with **both old and new** schemas
- ✅ Use Schema Registry to **enforce compatibility** at registration time
- ❌ Avoid removing fields without **deprecation period**

---

## Security Considerations

### Known Vulnerabilities

| Vulnerability Type | Mechanism | Impact | Affected Formats | Severity |
|-------------------|-----------|--------|------------------|----------|
| **Insecure Deserialization** | Malicious serialized objects execute code during deserialization | Remote Code Execution (RCE) | Java Serialization, Python pickle, PHP Serialization, .NET BinaryFormatter | **Critical** (OWASP Top 10) |
| **XML External Entity (XXE)** | XML parser processes external entity references | File disclosure, SSRF, DoS | XML | **High** |
| **YAML Deserialization** | YAML parsers execute arbitrary objects/functions | RCE | YAML (PyYAML, SnakeYAML) | **Critical** |
| **Object Injection** | User-controlled data deserialized into objects | Auth bypass, privilege escalation | PHP, Python pickle, Ruby Marshal | **High** |
| **Billion Laughs Attack** | Exponential entity expansion in XML | DoS (memory exhaustion) | XML | **High** |
| **Zip Bomb (via serialization)** | Compressed data expands exponentially | DoS (disk/CPU exhaustion) | Any compressed serialization | **Medium** |
| **Pickle RCE** | `__reduce__` method executes arbitrary code | RCE | Python pickle | **Critical** |

### Documented CVEs

| CVE | Year | Affected System | Format | Impact | CVSS | Links |
|-----|------|-----------------|--------|--------|------|-------|
| **CVE-2024-41874** | 2024 | Adobe ColdFusion | Untrusted data deserialization | RCE | N/A | [NVD](https://nvd.nist.gov/vuln/detail/cve-2024-41874) |
| **CVE-2024-11039** | 2024 | Python pickle-based systems | Pickle | Remote command execution | N/A | [CVE Details](https://www.cvedetails.com/cve/CVE-2024-11039/) |
| **CVE-2023-34040** | 2023 | Spring Framework (Java) | Java deserialization | RCE via exception record headers | N/A | [Spring](https://spring.io/security/cve-2023-34040/) |
| **CVE-2024-0692** | 2024 | H2 Database (Java) | Java deserialization | RCE | N/A | [OWASP](https://owasp.org/www-chapter-stuttgart/assets/slides/2024-12-10_Exploiting_deserialization_vulnerabilities_in_recent_Java_versions.pdf) |
| **CVE-2022-25857** | 2022 | Python packages | YAML (PyYAML) | RCE via yaml.load() | 8.0 | [NVD](https://nvd.nist.gov/vuln/detail/CVE-2022-25857) |
| **CVE-2017-12626** | 2017 | Apache Solr | YAML (SnakeYAML) | RCE | 9.8 | [NVD](https://nvd.nist.gov/vuln/detail/CVE-2017-12626) |

### Mitigation Strategies

| Strategy | Implementation | Effectiveness | Applicability |
|----------|----------------|---------------|---------------|
| **Never deserialize untrusted data** | Reject unknown sources | ✅ Complete | All formats |
| **Use schema-based formats** | Protobuf, Avro, FlatBuffers | ✅ High (type safety) | Cross-language systems |
| **Replace pickle with safe alternatives** | Use json, safetensors | ✅ High | Python, ML models |
| **Use yaml.safe_load() instead of yaml.load()** | PyYAML safe loader | ✅ High | Python YAML parsing |
| **Implement ObjectInputFilter (Java)** | Class allowlists | ✅ High | Java deserialization |
| **Disable external entities (XML)** | Parser configuration | ✅ High | XML parsing |
| **Validate input before deserialization** | Schema validation, checksums | ✅ High | All formats |
| **Use integrity checks** | HMAC signatures, checksums | ✅ High | Network transmission |
| **Limit payload size** | Maximum size enforcement | ✅ Medium | DoS prevention |
| **Keep libraries updated** | Patch management | ✅ Medium | All formats |
| **Use cryptographic seals** | SealedObject (Java) | ✅ High | Sensitive data |
| **Implement deserialization timeouts** | Time-limited parsing | ✅ Medium | DoS prevention |

**Security Resources:**
- [OWASP Deserialization Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Deserialization_Cheat_Sheet.html)
- [PortSwigger Deserialization Attacks](https://portswigger.net/web-security/deserialization)
- [Android Unsafe Deserialization](https://developer.android.com/privacy-and-security/risks/unsafe-deserialization)
- [Secure Deserialization of Pickle-based ML Models (ACM)](https://dl.acm.org/doi/10.1145/3719027.3765037)

---

## Standards & Specifications

### IETF RFC Standards

| Format | RFC Number | Title | Status | Links |
|--------|------------|-------|--------|-------|
| **JSON** | RFC 8259 | The JavaScript Object Notation (JSON) Data Interchange Format | Internet Standard (STD 90) | [RFC 8259](https://datatracker.ietf.org/doc/html/rfc8259) |
| **CBOR** | RFC 8949 | Concise Binary Object Representation (CBOR) | Proposed Standard | [RFC 8949](https://datatracker.ietf.org/doc/html/rfc8949) |
| **CBOR Serialization** | draft-ietf-cbor-serialization-04 | CBOR Serialization and Determinism | Internet-Draft | [Draft](https://datatracker.ietf.org/doc/html/draft-ietf-cbor-serialization-03) |
| **CSV** | RFC 4180 | Common Format and MIME Type for Comma-Separated Values | Informational | [RFC 4180](https://datatracker.ietf.org/doc/html/rfc4180) |
| **COSE** | RFC 8152 | CBOR Object Signing and Encryption (COSE) | Proposed Standard | [RFC 8152](https://datatracker.ietf.org/doc/html/rfc8152) |
| **JSON Patch** | RFC 6902 | JavaScript Object Notation (JSON) Patch | Proposed Standard | [RFC 6902](https://datatracker.ietf.org/doc/html/rfc6902) |
| **JSON Pointer** | RFC 6901 | JavaScript Object Notation (JSON) Pointer | Proposed Standard | [RFC 6901](https://datatracker.ietf.org/doc/html/rfc6901) |

### W3C Standards

| Format | Standard | Title | Status | Links |
|--------|----------|-------|--------|-------|
| **XML** | XML 1.0 (Fifth Edition) | Extensible Markup Language | W3C Recommendation | [W3C XML](https://www.w3.org/XML/) |
| **XML Schema (XSD)** | XML Schema 1.1 | W3C XML Schema Definition Language | W3C Recommendation | [XSD](https://www.w3.org/XML/Schema) |
| **Turtle** | Turtle 1.1 | Terse RDF Triple Language | W3C Recommendation | [Turtle](https://www.w3.org/TR/turtle/) |
| **JSON-LD** | JSON-LD 1.1 | A JSON-based Serialization for Linked Data | W3C Recommendation | [JSON-LD](https://www.w3.org/TR/json-ld11/) |
| **EXI** | Efficient XML Interchange (EXI) | Binary XML format | W3C Recommendation | [EXI](https://www.w3.org/TR/exi/) |

### ISO Standards

| Format | Standard | Title | Organization | Links |
|--------|----------|-------|--------------|-------|
| **ASN.1** | ITU-T X.680 series | Abstract Syntax Notation One | ITU-T / ISO | [ITU](https://www.itu.int/en/ITU-T/asn1/) |
| **XDR** | RFC 4506 / ISO | External Data Representation | IETF / ISO | [RFC 4506](https://datatracker.ietf.org/doc/html/rfc4506) |
| **CDR** | ISO/IEC 10866 | Common Data Representation | ISO | [ISO](https://www.iso.org/) |
| **STEP (ISO 10303)** | ISO 10303 | Product Data Representation and Exchange | ISO | [ISO 10303](https://www.iso.org/standard/63141.html) |

---

## Tools & Utilities

| Tool | Type | Formats | Platform | Description | Links |
|------|------|---------|----------|-------------|-------|
| **[protoc](https://github.com/protocolbuffers/protobuf)** | Compiler | Protobuf | Cross-platform | Protocol Buffers compiler | [GitHub](https://github.com/protocolbuffers/protobuf) |
| **[avro-tools](https://avro.apache.org/docs/current/gettingstartedjava.html#tools)** | CLI | Avro | JVM | Schema validation, conversion | [Website](https://avro.apache.org/) |
| **[jq](https://stedolan.github.io/jq/)** | CLI | JSON | Cross-platform | Command-line JSON processor | [Website](https://stedolan.github.io/jq/) |
| **[yq](https://github.com/mikefarah/yq)** | CLI | YAML, JSON, XML, TOML, CSV | Cross-platform | Command-line YAML processor | [GitHub](https://github.com/mikefarah/yq) |
| **[Apache Parquet Tools](https://parquet.apache.org/docs/file-format/)** | CLI | Parquet | JVM | Parquet file inspection | [Docs](https://parquet.apache.org/docs/file-format/) |
| **[HDFView](https://www.hdfgroup.org/downloads/hdfview/)** | GUI | HDF5 | Cross-platform | HDF5 file viewer and editor | [Download](https://www.hdfgroup.org/downloads/hdfview/) |
| **[JSON Schema Validator](https://www.jsonschemavalidator.net/)** | Web | JSON Schema | Browser | Online JSON Schema validation | [Website](https://www.jsonschemavalidator.net/) |
| **[Buf](https://buf.build/)** | CLI | Protobuf | Cross-platform | Modern Protobuf toolchain | [Website](https://buf.build/) |
| **[Wire](https://square.github.io/wire/)** | CLI/Library | Protobuf | JVM, Android | Square's lightweight Protobuf | [Website](https://square.github.io/wire/) |
| **[Prototool](https://github.com/uber/prototool)** | CLI | Protobuf | Cross-platform | Uber's Protobuf toolkit (archived) | [GitHub](https://github.com/uber/prototool) |
| **[Zebra](https://github.com/ColinSu/zebra)** | CLI | Parquet, ORC, Arrow | Cross-platform | Data file format viewer | [GitHub](https://github.com/ColinSu/zebra) |

---

## Learning Resources

### Technical Documentation

- [Protocol Buffers Language Guide](https://developers.google.com/protocol-buffers/docs/proto3) - Official Protobuf documentation
- [Apache Avro Specification](https://avro.apache.org/docs/current/spec.html) - Avro format specification
- [CBOR RFC 8949](https://datatracker.ietf.org/doc/html/rfc8949) - IETF CBOR specification
- [JSON RFC 8259](https://datatracker.ietf.org/doc/html/rfc8259) - IETF JSON specification
- [YAML 1.2.2 Specification](https://yaml.org/spec/1.2.2/) - Official YAML specification
- [MessagePack Specification](https://github.com/msgpack/msgpack/blob/master/spec.md) - MessagePack format specification
- [FlatBuffers Documentation](https://flatbuffers.dev/) - Official FlatBuffers guide
- [Cap'n Proto Style Guide](https://capnproto.org/language.html) - Cap'n Proto language reference
- [Apache Arrow Format Specification](https://arrow.apache.org/docs/format/Columnar.html) - Arrow columnar format
- [Serde Documentation](https://serde.rs/) - Rust serialization framework

### Research Papers

- [Performance Comparison of Messaging Protocols and Serialization Formats](https://www.ida.liu.se/~nikca89/papers/networking20c.pdf) - Proos et al., 2020 (65 citations)
- [Secure Deserialization of Pickle-based Machine Learning Models](https://dl.acm.org/doi/10.1145/3719027.3765037) - ACM Conference Paper, 2025
- [Overview of Serialization Technologies (CERN Indico)](https://indico.cern.ch/event/658060/contributions/2898569/attachments/1622526/2582399/pivarski-serialization.pdf) - Pivarski, 2018
- [Comparison of Data Serialization Formats (Wikipedia)](https://en.wikipedia.org/wiki/Comparison_of_data-serialization_formats) - Comprehensive comparison table
- [Heep: An FPGA-accelerated Reader for Apache Parquet](https://www.research-collection.ethz.ch/bitstreams/1365f9df-38d0-42f8-b32c-ee1fd40047b5/download) - ETH Zürich, 2025
- [Benchmarking Apache Arrow Flight](https://dl.acm.org/doi/fullHtml/10.1145/3527199.3527264) - ACM Conference Paper
- [Evaluating Serialization Formats for Space-Efficient Storage](https://science.lpnu.ua/sites/default/files/journal-paper/2024/jun/35114/vse200624doi-11-17.pdf) - 2024 study

- [eishay/jvm-serializers](https://github.com/eishay/jvm-serializers) - JVM serialization
- [ProgrammerAL/SerializationBenchmarks](https://github.com/ProgrammerAL/SerializationBenchmarks) - C#/.NET

---

## Related Awesome Lists

- [awesome-json](https://github.com/burningtree/awesome-json) - Curated list of JSON libraries and resources
- [awesome-serialization](https://github.com/maximveksler/awesome-serialization) - Curated list of serialization formats
- [awesome-xml](https://github.com/StanimirIglev/awesome-xml) - Curated list of XML standards and libraries
- [awesome-cpp](https://github.com/fffaraz/awesome-cpp#serialization) - C++ libraries (serialization section)
- [awesome-python](https://github.com/vinta/awesome-python#serialization) - Python libraries (serialization section)
- [awesome-go](https://github.com/avelino/awesome-go#serialization) - Go libraries (serialization section)
- [awesome-rust](https://github.com/rust-unofficial/awesome-rust#serialization) - Rust libraries (serialization section)
- [awesome-hessian](https://github.com/hessian-group/awesome-hessian) - Hessian serialization resources

---

## Contributing

Contributions are welcome! Please submit a Pull Request or open an Issue to suggest additions or changes.

**Contribution Guidelines:**
- Provide links to official documentation, RFCs, or specifications
- Note security implications when relevant
- Specify licenses for libraries
- Indicate language/version compatibility

---

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, the contributors have waived all copyright and related or neighboring rights to this work.

---

**Have a suggestion?** Open an issue or submit a pull request!
