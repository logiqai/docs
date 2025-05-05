---
description: Decoding methods for data in Ascent
---

# ascent.decode

### Ascent.decode - Data Decoding Methods

#### Apica.decode.base64

decodes a string in Base64 format.

```typescript
ascent.decode.b64(input:string):string;
```

| Parameter | Type   | Description     |
| --------- | ------ | --------------- |
| string    | string | Value to decode |

Examples

To base64-encode the username

```
Event.decode = Ascent.decode.b64("Username")
```

#### Ascent.decode.gzip

Compress a string using Gzip. Output a base64 encode string

```
ascent.decode.gzip(input: string): string;
```

| Parameter | Type   | Description     |
| --------- | ------ | --------------- |
| string    | string | Value to encode |

Examples

To encode the username

```
Event.decode =  Ascent.decode.b64("Username");
```

#### Ascent.decode.uri

Encodes a string using URI encoding

```
Ascent.decode.uri(input: string): string;
```

| Parameter | Type   | Description     |
| --------- | ------ | --------------- |
| string    | string | Value to encode |

Examples

To decode the username

```
Event.decode =  Ascent.decode.uri("Username");
```

#### Ascent.decode.hex

decodes a string in Hexadecimal format.

```
Ascent.decode.hex(input: String): String
```

| Parameter | Type   | Description     |
| --------- | ------ | --------------- |
| string    | string | Value to encode |

Examples

To decode the username

```
Event.decode =  Ascent.decode.hex("Username");
```
