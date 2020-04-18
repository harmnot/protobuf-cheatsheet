## Protobuf



#### create request and respond

```protobuf
syntax = "proto3"

// array : ["string", "string"]
message ArrayStr {
	repeated string key = 1
}

// { name: "MY_NAME", gender: "MY_GENDER" }
message MyData {
	string name = 1
	string gender = 2
}

message Company {
	string name = 1
	string address = 2
}

// object in array : [ { name: "MY_NAME", gender: "MY_GENDER" } ]
message ArrayObject {
	repeated MyData format_data = 1
}

// array in object then array in object
// {
// 	username: "MY_NAME",
// 	password: "PASSWORD",
// 	hobbies: ["Swim", "Gym"],
// 	familes: [ { name: "DADDY_NAME", gender: "MAN" } ]
// 	other: { key: "VALUE" }
// }
message ListData {
	string username = 1
	string password = 2
	
	oneof payload {
		repeated ArrayStr hobbies = 3
		ArrayObject families = 4
		ArrayStr other = 5
	}
}


// Any 
import "google/protobuf/any.proto";

message ErrorStatus {
  string message = 1;
  repeated google.protobuf.Any details = 2;
}

// Object with spesific value
message Myself {
	string name = 1
	map<string, MyData> data = 2;
}

// ENUM
message Role {
	string name = 1
	enum SpesificRole {
		root = 0
		admin = 1
		member = 2
	}
	
	SpesificRole as = 2
}

// ListValue
message ListObjects {
	ListValue information 
}
```

