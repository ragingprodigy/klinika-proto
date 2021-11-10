# eyowo-proto

Protobuf Documentation: [developers.google.com/protocol-buffers/docs/overview](https://developers.google.com/protocol-buffers/docs/overview)

## Guide

- All proto files belonging to a service should be saved to a single directory.

- The directory name should correspond to the name of the service whose files it contains (e.g. user, developer, admin).

- All proto files in a directory should declare the package as the name of the directory (service).

```proto
package <service_name>;
```

- The names of service methods and messages should be in PascalCase to ensure they are exported correctly in the generated code.

```proto
service Admin {
  rpc Search(SearchRequest) returns(SearchResponse);
}

message SearchRequest { // not `searchRequest`
  string query = 1;
}

message SearchResponse { // not `searchResponse`
  message Data { // not `data`
    bool success = 1;
  }
  Data data = 1;
}
```

- Imports should be prefixed with the package name of the imported package.

```proto
import "models/models.proto";

message People {
  repeated models.Person = 1; // not `Person`
}
```
